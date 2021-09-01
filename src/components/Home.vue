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
    <div id="input-group">
      <input
        type="text"
        placeholder="Enter a hotel name or destination"
        id="hotel-name"
      /><input type="date" class="date" /><input
        type="date"
        class="date"
      /><input type="number" placeholder="Number of guests" />
      <button>Search</button>
    </div>
    <button @click="emitToApp">FAQ about Bookings</button>
  </div>
  <Footer />
  <Copyright />
</template>

<script>
import Navbar from "./Navbar.vue";
import Footer from "./Footer.vue";
import Copyright from "./Copyright.vue";
export default {
  components: {
    Navbar,
    Footer,
    Copyright,
  },
  methods: {
    emitToApp() {
      this.$emit("gotoBookings");
    },
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
p {
  margin: 0;
}
h2 {
  margin-bottom: 0;
}
.left-border {
  padding-left: 20px;
  border-left: 1px solid rgba(128, 128, 128, 0.233);
  margin-top: 2%;
}
#input-group {
  border-radius: 7px;
  box-shadow: 1px 1px 2px 1px rgb(173, 173, 173);
  padding: 10px 0;
  margin: 2% 5%;

  text-align: center;
  display: flex;
  flex-wrap: wrap;
  background-color: white;
  /* width: auto; */
}
input {
  border: none;
  border-right: 1px solid rgba(128, 128, 128, 0.356);
  margin: 1% 2%;
}
#hotel-name {
  width: 19%;
  margin: 0;
  margin-left: 2%;
  min-width: 230px;
}
.date {
  margin-right: 0;
  min-width: 140px;
}
button {
  border-radius: 20px;
  border: 1px solid rgba(128, 128, 128, 0.397);
  background-color: RGB(0, 127, 173);
  color: white;
  margin: 1% 2%;
  width: 20%;
  height: 40px;
  font-weight: bold;
  margin: auto;
  font-family: "Poppins";
}
#search {
  background-color: RGB(245, 245, 246);
  padding: 20px;
  margin: 2% 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  /* align-items: center; */
}
</style>