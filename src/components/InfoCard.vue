<template>
  <div class="card-container">
    <img v-bind:src="imgSrc" />
    <div class="message-container">
      <h2>{{ "Hotels In " + location }}</h2>
      <span class="lower-row">
        <p class="message">{{ message }}</p>
        <p class="price">{{ "Avg. $" + avgPrice }}</p>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["imgSrc", "location", "message", "avgPrice"],
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300&display=swap");
.card-container {
  display: flex;
  flex-direction: column;
  font-family: "Poppins";
  width: 258px;
  box-shadow: 1px 1px 10px 1px #00000069;
  border-radius: 20px;
  padding: 5px;
  /* height: auto; */
  /* border: 2px solid black; */
}
img {
  height: 258px;
  border-radius: 20px;
  box-shadow: 1px 1px 10px 1px #00000069;
}
.message-container {
  padding-left: 8px;
}
h2 {
  /* border: 2px solid black; */
  margin-bottom: 0;
}
p {
  font-size: 1.1em;
  margin-right: 15px;
}
.message {
  font-weight: 500;
}
.price {
  font-weight: 700;
  color: rgb(3, 148, 3);
}
.lower-row {
  display: flex;
  /* border: 2px solid black; */
}
</style>