<template>
  <ul>
    <li id="chosen">Bookings</li>
    <li>Searching on trivago</li>
    <li>Get in touch</li>
    <li>How trivago Works</li>
  </ul>
</template>

<script>
export default {};
</script>

<style scoped>
ul {
  display: flex;
  justify-content: flex-start;
  border-top: 0.2px solid rgba(207, 207, 207, 0.623);
  border-bottom: 0.2px solid rgba(207, 207, 207, 0.623);
  padding: 0 5%;
  margin-left: auto;
  margin-right: auto;
  width: auto;
  list-style-type: none;
}
li {
  color: rgb(74, 85, 118);
  transition: 200ms;
  padding: 1.5%;
  margin-left: 2%;
  display: flex;
  align-items: center;
  flex-direction: column;
  font-size: 0.9em;
  font-weight: bold;
  border-bottom: 3px solid rgba(43, 107, 202, 0);
  border-radius: 2px;
}
li:hover {
  color: black;
  transition: 200ms;
  cursor: pointer;
  border-bottom: 3px solid rgba(160, 160, 160, 0.596);
}
#chosen {
  border-bottom: 3px solid rgb(43, 107, 202);
  border-radius: 2px;
}
</style>