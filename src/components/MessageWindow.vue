<template>
  <div>
    <h2>Couldn't find your answer?</h2>
    <p>We're here to help</p>
    <button>Submit a request</button>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300&display=swap");

div {
  border: 1px solid rgba(128, 128, 128, 0.432);
  border-radius: 6px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  height: 1%;
  margin-right: 1%;
  margin-top: 2%;
  min-width: 25%;
}
h2 {
  font-size: 1.2em;
  margin: 0;
}
button {
  background-color: white;
  border: 1px solid rgba(128, 128, 128, 0.432);
  width: 100%;
  border-radius: 5px;
  padding: 10px;
  font-family: "Poppins";
  color: RGB(0, 168, 215);
}
@media only screen and (max-width: 1045px) {
  div {
    margin: 0 7%;
  }
}
</style>