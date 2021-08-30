<template>
  <div class="wrapper" @click="toggleVisible">
    <h2>{{ question }}</h2>
    <div class="answer" v-show="this.isVisible">
      <p>{{ answer }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isVisible: false,
    };
  },
  props: ["question", "answer"],
  methods: {
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
  },
};
</script>

<style scoped>
.wrapper {
  transition: 1s;
  background-color: rgb(247, 250, 252);
  box-shadow: 1px 1px 2px 1px #0000001e;
  border-radius: 5px;
  padding: 0.5% 5%;
  margin: 2% 7%;
}
h2 {
  font-size: 1.1em;
  color: rgb(74, 85, 118);
}
h2:hover {
  cursor: pointer;
}
</style>