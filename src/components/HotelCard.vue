<template>
  <div id="main-container">
    <div id="img-container">
      <img src="https://via.placeholder.com/211" alt="" />
    </div>
    <div id="hotel-info">
      <h2>{{ response.hotel.name }}</h2>
      <div>
        <Star v-if="response.hotel.rating >= 1" />
        <Star v-if="response.hotel.rating >= 2" />
        <Star v-if="response.hotel.rating >= 3" />
        <Star v-if="response.hotel.rating >= 4" />
        <Star v-if="response.hotel.rating >= 5" />
      </div>
      <p>
        {{
          response.hotel.hotelDistance.distance +
          " " +
          response.hotel.hotelDistance.distanceUnit +
          " to city center"
        }}
      </p>
    </div>
    <div id="price">
      <p>
        {{
          "Total Price : " +
          response.offers[0].price.total +
          "" +
          response.offers[0].price.currency
        }}
      </p>
    </div>
  </div>
</template>

<script>
import Star from "./Star.vue";
export default {
  props: ["response"],
  components: { Star },
};
</script>

<style scoped>
#main-container {
  width: 55%;
  height: 211px;
  padding: 20px;
  display: flex;
  border-radius: 10px;
  box-shadow: 1px 1px 2px 1px grey;
  margin: 2% auto;
  background: linear-gradient(to left, rgb(16, 197, 197), rgb(6, 98, 134));
}
h2,
p {
  color: white;
}
img {
  border-radius: 10px;
  box-shadow: 1px 1px 1px 1px grey;
}
#img-container {
  margin: 0 1.5%;
}
</style>