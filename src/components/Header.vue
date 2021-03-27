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
    font-size: 100px;
    padding: 0px;
    margin: 0px;
  }
  img {
    position: center;
    max-width: 30%;
    padding: 0px;
    margin: 0px;
  }

</style>