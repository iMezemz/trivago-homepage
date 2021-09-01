<template>
  <Header @gotoHome="emitToHome" />
  <Navbar />
  <MainWindow />
  <Footer />
  <Copyright />
  <div v-if="this.createAccountVisible">
    <CreateAccount @closePrompt="toggleCreateAccountPrompt" />
  </div>
  <div id="buttons-container">
    <button @click="toggleCreateAccountPrompt" class="user-login-button">
      Create an account
    </button>
    <button class="user-login-button">Log in</button>
  </div>
</template>

<script>
import MainWindow from "./../components/MainWindow.vue";
import Header from "./../components/Header.vue";
import Navbar from "./../components/Navbar.vue";
import MessageWindow from "./../components/MessageWindow.vue";
import Footer from "./../components/Footer.vue";
import Copyright from "./../components/Copyright.vue";
import CreateAccount from "./../components/CreateAccount.vue";
export default {
  components: {
    Header,
    Navbar,
    MessageWindow,
    MainWindow,
    Footer,
    Copyright,
    CreateAccount,
  },
  data() {
    return {
      createAccountVisible: false,
    };
  },
  methods: {
    toggleCreateAccountPrompt() {
      this.createAccountVisible = !this.createAccountVisible;
    },
    emitToHome() {
      this.$emit("activateHomeView");
    },
  },
};
</script>

<style>
.user-login-button {
  padding: 10px;
  margin: 0 5%;
  background-color: rgb(78, 101, 114);
  border: 1px solid rgba(201, 205, 207, 0.603);
  border-radius: 25px;
  color: white;
  min-width: 10%;
}
.user-login-button:hover {
  transition: 1s;
  transform: scale(1.1);
  background-color: rgb(92, 115, 128);
  cursor: pointer;
}
#buttons-container {
  display: flex;
  justify-content: center;
  padding: 20px;
  background-color: rgb(55, 69, 77);
  padding-top: 0;
}
</style>