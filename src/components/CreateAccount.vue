<template>
  <div class="backdrop">
    <div class="prompt-container">
      <div id="upper-row">
        <button @click="closePrompt" id="close-prompt">
          <img class="left-chevron" src="./../assets/left.png" />
        </button>
        <div class="img-container">
          <img
            src="https://theme.zdassets.com/theme_assets/196898/9addc16d02ae592b532d01410947d206e21ac2bf.png"
            alt=""
          />
        </div>
      </div>
      <div class="main-input-view">
        <h2>Create Your Account</h2>
        <p>Add a strong password to finish up</p>

        <h4>Email Address</h4>
        <input type="email" name="email" placeholder="Email address" id="" />

        <h4>Password</h4>
        <input type="password" name="password" placeholder="Password" id="" />

        <ul>
          <li>Lowercase letter</li>
          <li>Uppercase letter</li>
          <li>Number</li>
          <li>Special character</li>
          <li>Min. 12 characters</li>
        </ul>
        <button id="register">Register</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    closePrompt() {
      this.$emit("closePrompt");
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300&display=swap");

.backdrop {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  background-color: rgba(104, 104, 104, 0.562);
}
.prompt-container {
  position: fixed;
  width: 50%;
  height: auto;
  top: 10%;
  left: 25%;
  background-color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  box-shadow: 1px 1px 5px 1px #0000001e;
  border-radius: 20px;
}
#upper-row {
  display: flex;
}
h4 {
  margin-bottom: 0;
  font-size: 0.9em;
}
input {
  width: 65%;
  padding: 10px;
}
#close-prompt {
  width: 10%;
  min-width: 80px;
  border: none;
  padding: 10px;
  height: 64px;
  background-color: white;
}
.img-container {
  display: flex;
  justify-content: center;
  width: 90%;
  background-color: white;
}
img {
  padding-right: 10%;
  width: 155px;
  height: 64px;
  transform: scale(0.8);
}
.left-chevron {
  padding-right: 0;
  width: 10%;
  height: auto;
  transform: scale(4);
}
.main-input-view {
  padding: 0 5%;
  padding-left: 40px;
}
#register {
  width: 200px;
  height: 50px;
  background-color: rgb(0, 110, 255);
  color: white;
  font-family: "Poppins";
  border: 1px solid rgba(128, 128, 128, 0.63);
  border-radius: 10px;
}
#register:hover {
  transition: 500ms;
  transform: scale(1.1);
}
</style>