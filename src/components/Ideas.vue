<template>
  <div class="container">
    <div v-bind:key="idea.id" v-for="idea in ideas">
      <IdeaItem v-bind:idea="idea" v-on:del-idea="$emit('del-idea', idea.id)" @update-idea="$emit('update-idea', editedIdea)"/>
    </div>
  </div>
</template>

<script>
  import IdeaItem from './IdeaItem.vue';

  export default {
    name: "Ideas",
    components: {
      IdeaItem
    },

    props: ["ideas"]
  }

</script>

<style scoped>
  .container {
    margin: 20px;
    padding: 10px;
    display: flex;
    align-items: row;
    background-color: lightgray;
    flex-wrap: wrap;
    opacity: 90%;
  }
  .container > div {
  margin: 10px;
}
</style>