<template>
  <div id="main-div">
    <FaqList title="Bookings" />
    <MessageWindow />
  </div>
</template>

<script>
import MessageWindow from "./MessageWindow.vue";
import FaqList from "./FaqList.vue";
export default {
  components: { MessageWindow, FaqList },
};
</script>

<style scoped>
#main-div {
  display: flex;
  justify-content: space-between;
}
@media only screen and (max-width: 1045px) {
  #main-div {
    flex-direction: column;
  }
}
</style>