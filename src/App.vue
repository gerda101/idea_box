<template>
  <div id="app" class="app">
    <Header/>
    <Ideas v-bind:ideas="ideas" v-on:del-idea="deleteIdea" />
    <AddIdea v-on:add-idea='addIdea' />
  </div>
</template>

<script>
  import Header from './components/Header';
  import Ideas from './components/Ideas';
  import AddIdea from './components/AddIdea';

  export default {
    name: 'App',

    components: {
      Header,
      Ideas,
      AddIdea
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
      },
      addIdea(newIdea){
        this.ideas = [...this.ideas, newIdea];
      }
    }
  }
</script>

<style>
  * {
    line-height: 1.4;
    border-radius: 20px;
  }

  .app {
    font-family: Lora, serif;
    margin: auto;
    margin-top: 20px;
    width: 70%;
    border: 2px lightgrey dotted;
    padding: 10px;
  }

  .btn {
    background: lightseagreen;
    cursor: pointer;
  }
</style>
