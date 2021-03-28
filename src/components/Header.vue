<template>
  <header class="header">
    <img src="../assets/idea_box.png" alt="Logo">
    <h1>IdeaBox</h1>
  </header>
</template>

<script>
  export default {
    name: "Header"
  }

</script>

<style scoped>
  .header {
    font-family: 'Abril Fatface', serif;
    text-align: center;
    padding: 0px;
    margin: 0px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  h1 {
    font-size: 10vw;
    padding: 0px;
    margin: 0px;
    opacity: 70%;
  }
  img {
    position: center;
    min-width: 10%;
    max-width: 30%;
    padding: 0px;
    margin: 0px;
  }

</style>