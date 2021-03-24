<template>
  <div>
    <div v-bind:key="idea.id" v-for="idea in ideas">
      <IdeaItem v-bind:idea="idea" v-on:del-idea="$emit('del-idea', idea.id)"/>
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
  
</style>