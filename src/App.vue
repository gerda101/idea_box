<template>
  <div id="app">
    <Header/>
    <Ideas v-bind:ideas="ideas" v-on:del-idea="deleteIdea" />
  </div>
</template>

<script>
  import Header from './components/Header';
  import Ideas from './components/Ideas';

  export default {
    name: 'App',

    components: {
      Header,
      Ideas
    },

    data() {
      return {
        ideas: [
          {
            id: 1,
            text: "Test idea 1"
          },
          {
            id: 2,
            text: "Test idea 2"
          },
          {
            id: 3,
            text: "Test idea 3"
          }
        ]
      }
    },

    methods: {
      deleteIdea(id) {
        this.ideas = this.ideas.filter(idea => idea.id !== id);
      }
    }
  }
</script>

<style>
  body {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    line-height: 1.4;
  }
</style>
