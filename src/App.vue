<template>
  <Header />
  <Navbar />
  <MainWindow />
  <Footer />
  <Copyright />
  <!-- <MessageWindow /> -->
  <!-- <FaqList title="Bookings" /> -->
</template>

<script>
import MainWindow from "./components/MainWindow.vue";
import Header from "./components/Header.vue";
import Navbar from "./components/Navbar.vue";
import MessageWindow from "./components/MessageWindow.vue";
import FaqList from "./components/FaqList.vue";
import Footer from "./components/Footer.vue";
import Copyright from "./components/Copyright.vue";
export default {
  name: "App",
  components: {
    Header,
    Navbar,
    FaqList,
    MessageWindow,
    MainWindow,
    Footer,
    Copyright,
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
