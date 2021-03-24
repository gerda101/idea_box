<template>
  <div>
    <p class="idea-item">
      <input type="checkbox" v-on:change="selected"/>
      {{idea.text}}
      <button @click="$emit('del-idea', idea.id)">x</button>
    </p>
  </div>
</template>

<script>
  export default {
    name: "IdeaItem",
    props: ["idea"],

    methods: {
      selected() {
        console.log("selected");
      }

    }
  }

</script>

<style scoped>
  .idea-item {
    background: #0094ff;
    padding: 10px;
  }
  .is-selected {
    border: groove;
  }
</style>