<template>
  <div
    style="
      background-color: rgb(41, 52, 58);
      margin: 0;
      padding: 2% 15%;
      margin-top: 4%;
    "
  >
    <div style="display: flex; justify-content: space-between">
      <p>trivago N.V., Kesselstraße 5 – 7, 40221 Düsseldorf, Germany</p>
      <span style="border: 1px solid white">
        <p>English (US)</p>
      </span>
    </div>
    <!-- <div>
      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </div> -->
    <div id="links-wrapper">
      <ul>
        <li>Company</li>
        <li>Jobs</li>
        <li>Press</li>
        <li>Investor Relations</li>
      </ul>
      <ul>
        <li>Mobile Apps - Search on the go</li>
        <li>trivago Business Studio</li>
        <li>trivago Magazine</li>
      </ul>
      <ul>
        <li>Terms and Conditions</li>
        <li>Legal Information</li>
        <li>Privacy Policy</li>
        <li>Cookie Policy</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
li,
p {
  color: white;
}
span {
  min-width: 25%;
  padding-left: 2%;
}
ul {
  list-style: none;
  margin-right: 6%;
}
#links-wrapper {
  display: flex;
  justify-content: flex-start;
}
li:hover {
  text-decoration: underline;
  cursor: pointer;
}
</style>