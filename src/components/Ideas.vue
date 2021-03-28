<template>
  <div class="container">
    <div v-bind:key="idea.id" v-for="idea in ideas">
      <IdeaItem v-bind:idea="idea" v-on:del-idea="$emit('del-idea', idea.id)" @event:show-event="$emit('show-event', true, false)"/>
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
    props: ["ideas"],
  }

</script>

<style scoped>
  .container {
    margin: 20px;
    padding: 10px;
    display: flex;
    align-items: row;
    justify-items: normal;
    background-color: lightgray;
    opacity: 70%;
    flex-wrap: wrap;
  }
  .container > div {
  margin: 10px;
  opacity: 100%;
}
</style>