<template>
  <Navbar />
  <div id="head">
    <div id="logo-container">
      <img
        src="https://theme.zdassets.com/theme_assets/196898/9addc16d02ae592b532d01410947d206e21ac2bf.png"
        alt=""
      />
    </div>
    <div class="left-border">
      <h2>Deals from your favorite booking sites. All in one place.</h2>
      <p>Try searching for a city, a specific hotel, or even a landmark!</p>
    </div>
  </div>
  <div id="search">
    <div id="input-group" v-if="!searchInitiated">
      <h2 style="text-align: center">Find your next stay!</h2>
      <div id="hotel-name" class="text-input">
        <h3>Search By Hotel Name</h3>
        <input
          type="text"
          placeholder="Enter a hotel name or destination"
          id="hotel-name"
          v-model="this.hotelName"
        />
      </div>
      <div id="date-pick" class="text-input">
        <h3>Pick the dates of your stay</h3>
        <input
          type="date"
          class="date"
          id="start-date"
          v-model="startDate"
          @change="update"
        />
        <input
          type="date"
          class="date"
          id="end-date"
          v-model="endDate"
          @change="update"
        />
      </div>
      <div id="guest-num" class="text-input">
        <h3>How many adults are staying?</h3>
        <input
          type="number"
          v-model="this.guestNumber"
          placeholder="Number of guests"
          min="1"
          max="9"
        />
      </div>
      <div id="pick-price" class="text-input">
        <h3>Pick a budget range</h3>
        <p>(Per Night)</p>
        <input type="range" id="min-price" v-model="minPrice" step="100" />
        <input
          type="range"
          id="max-price"
          v-model="maxPrice"
          step="100"
          max="20000"
        />
        <p v-if="this.minPrice == 0 && this.maxPrice == this.minPrice">
          Price Range : Any
        </p>
        <p v-else>
          {{
            "Price Range : " + this.minPrice + " - " + this.maxPrice + " EGP"
          }}
        </p>
      </div>
      <div id="board-type" class="text-input">
        <h3>Choose a board type</h3>
        <select name="Board Type" id="board-type" v-model="this.boardType">
          <option value="">All</option>
          <option value="ROOM_ONLY">Room Only</option>
          <option value="BREAKFAST">Breakfast</option>
          <option value="HALF_BOARD">Half Board</option>
          <option value="FULL_BOARD">Full Board</option>
          <option value="ALL_INCLUSIVE">All Inclusive</option>
        </select>
      </div>
      <button @click="fetchHotels">Search</button>
    </div>
    <button @click="emitToApp">FAQ about Bookings</button>
    <div id="results" v-if="searchInitiated"></div>
    <h2 v-if="searchResults.length == 0 && searchInitiated">
      No Results Found...
    </h2>
    <HotelCard
      :key="response.hotel.dupeId"
      v-for="response in searchResults"
      :response="response"
    />
    <button v-if="searchInitiated" @click="reset">Reset Search</button>
  </div>
  <Footer />
  <Copyright />
</template>

<script>
import Navbar from "./Navbar.vue";
import Footer from "./Footer.vue";
import Copyright from "./Copyright.vue";
import HotelCard from "./HotelCard.vue";

export default {
  data() {
    return {
      hotelName: "",
      startDate: "",
      endDate: "",
      guestNumber: 1,
      minPrice: 0,
      maxPrice: 2000,
      boardType: "",
      searchInitiated: false,
      searchResults: [],
    };
  },
  components: {
    Navbar,
    Footer,
    Copyright,
    HotelCard,
  },
  methods: {
    reset() {
      (this.searchResults = []), (this.searchInitiated = false);
    },
    update() {
      this.$forceUpdate();
    },
    emitToApp() {
      this.$emit("gotoBookings");
    },
    incDay(date, n) {
      let fudate = new Date(
        new Date(date).setDate(new Date(date).getDate() + n)
      );
      fudate =
        fudate.getFullYear() +
        "-" +
        (fudate.getMonth() + 1) +
        "-" +
        fudate.toDateString().substring(8, 10);
      return fudate;
    },
    async fetchHotels() {
      let searchQuery = "";
      if (this.hotelName != "") {
        searchQuery += "&hotelName=" + this.hotelName.split(" ").join("%");
      }
      if (this.startDate != this.endDate) {
        searchQuery +=
          "&checkInDate=" + this.startDate + "&checkOutDate=" + this.endDate;
      }
      searchQuery += "&adults=" + this.guestNumber;
      if (this.minPrice != this.maxPrice) {
        searchQuery += "&priceRange=" + this.minPrice + "-" + this.maxPrice;
      }
      // searchQuery+="&boardType="+this.boardType;
      const response = await fetch(
        "https://test.api.amadeus.com/v2/shopping/hotel-offers?cityCode=CAI&roomQuantity=1&radius=100&radiusUnit=KM&currency=EGP&paymentPolicy=NONE&includeClosed=false&" +
          searchQuery,
        {
          method: "GET",
          headers: { Authorization: "Bearer VDGt59Riph4xDiafawmnnqZGDJae" },
        }
      );
      const json = await response.json();
      this.searchResults = json.data;
      console.log(this.searchResults);
      this.searchInitiated = true;
    },
  },
  mounted() {
    //initiallizing dates
    let today = new Date();
    let todaysDate = today.getFullYear() + "-";
    todaysDate +=
      today.getMonth() + 1 < 10
        ? "0" + (today.getMonth() + 1)
        : today.getMonth() + 1;
    todaysDate +=
      today.getDate() < 10 ? "-0" + today.getDate() : "-" + today.getDate();
    let tomorrowsDate = this.incDay(todaysDate, 1)
      .split("-")
      .map((num) => (num.length == 1 ? "0" + num : num))
      .join("-");
    this.startDate = todaysDate;
    this.endDate = tomorrowsDate;
    document.getElementById("start-date").setAttribute("min", todaysDate);

    //initiallizing price range
    document.getElementById("min-price").setAttribute("max", this.maxPrice);
    document.getElementById("min-price").setAttribute("min", this.minPrice);
  },
  updated() {
    //update date fields
    if (!this.searchInitiated) {
      let min = this.incDay(this.startDate, 1)
        .split("-")
        .map((num) => (num.length == 1 ? "0" + num : num))
        .join("-");
      document.getElementById("start-date").setAttribute("max", this.endDate);
      document.getElementById("end-date").setAttribute("min", min);
      console.log(this.endDate);
      //update price ranges

      document.getElementById("min-price").setAttribute("max", this.maxPrice);
      document.getElementById("max-price").setAttribute("min", this.minPrice);
    }
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300&display=swap");

ul {
  margin-top: 0px;
}
img {
  width: 180px;
}
#head {
  display: flex;
  justify-content: center;
  flex-wrap: nowrap;
}
#logo-container {
  display: flex;
  align-items: center;
}
.left-border p {
  margin: 0;
}
h2 {
  margin-bottom: 0;
}
h3 {
  margin-left: 2%;
  font-weight: 200;
}
.text-input p {
  display: flex;
  align-items: center;
  font-weight: 100;
}
.left-border {
  padding-left: 20px;
  border-left: 1px solid rgba(128, 128, 128, 0.233);
  margin-top: 2%;
}
#input-group {
  border-radius: 7px;
  box-shadow: 1px 1px 2px 1px rgb(173, 173, 173);
  display: flex;
  flex-direction: column;
  padding: 30px;
  margin: 5% 5%;
  background: linear-gradient(to left, rgb(16, 197, 197), rgb(6, 98, 134));
}
.text-input {
  display: flex;
  margin: 2%;
  /* border: 2px solid black; */
}
#input-group h2,
#input-group h3,
#input-group p {
  color: white;
}
button {
  border-radius: 20px;
  border: 1px solid rgba(128, 128, 128, 0.397);
  color: rgb(255, 255, 255);
  /* font-weight: bold; */
  font-family: "Poppins";
  width: 25%;
  height: 40px;
  background-color: rgb(196, 4, 30);
}
#input-group button {
  width: 30%;
  height: 50px;
  margin: auto;
}

#hotel-name input,
#guest-num input,
#board-type select,
#date-pick input {
  height: 40px;
  margin: 10px;
  width: 50%;
  border: 1px solid rgba(128, 128, 128, 0.418);
  padding: 2px;
  text-align: center;
  border-radius: 10px;
  box-shadow: 1px 1px 2px 1px rgb(173, 173, 173);
  background-color: rgba(245, 245, 245, 0.856);
}
#search {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>