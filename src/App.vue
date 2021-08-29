<template>
  <InfoCard
    imgSrc="https://images.unsplash.com/photo-1512850183-6d7990f42385?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=934&q=80"
    location="New York"
    message="8117 Hotels"
    avgPrice="255"
  />
</template>

<script>
import "./components/InfoCard.vue";
import InfoCard from "./components/InfoCard.vue";
export default {
  name: "App",
  components: {
    InfoCard,
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
}
</style>
