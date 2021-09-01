<template>
  <Bookings @activateHomeView="toggleView" v-if="!HomeView" />
  <Home @gotoBookings="toggleView" v-if="HomeView" />
</template>

<script>
import Bookings from "./components/Bookings.vue";
import Home from "./components/Home.vue";
export default {
  name: "App",
  data() {
    return {
      HomeView: true,
    };
  },
  components: {
    Bookings,
    Home,
  },
  methods: {
    toggleView() {
      this.HomeView = !this.HomeView;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300&display=swap");

#app {
  font-family: "Poppins";
}
body {
  margin: 0;
}
</style>
