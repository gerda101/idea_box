<template>
  <div id="app" class="app" v-on:show-event='showDecider'>
    <Header/>
    <AddIdea v-on:add-idea='addIdea' v-show="showNew"/>
    <EditIdea v-on:edit-idea='editIdea' v-show="showEdit"/>
    <Ideas v-bind:ideas="ideas" v-on:del-idea="deleteIdea" />
    <p class="footer">Made by Gerda Urbán in 2021</p>
  </div>
</template>

<script>
  import Header from './components/Header';
  import Ideas from './components/Ideas';
  import AddIdea from './components/AddIdea';
  import EditIdea from './components/EditIdea';

  export default {
    name: 'App',

    components: {
      Header,
      Ideas,
      AddIdea,
      EditIdea
    },

    data() {
      return {
        showNew: true,
        showEdit: false,
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
      },
      editIdea(oldId, editedIdea){
        this.ideas = this.ideas.filter(idea => idea.id !== oldId);
        this.ideas = [...this.ideas, editedIdea];
      },
      showDecider(edit, add) {
        this.showEdit = edit;
        this.showNew = add;
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
    background: #eb9b45;
    opacity: 90%;
    cursor: pointer;
    border: 0px;
    padding-right: 10px;
    padding-left: 10px;
  }
  .btn:hover {
    opacity: 100%;
    box-shadow: 2px 1px lightgrey;
  }

  form{
  display: flex;
  flex-direction: row;
  justify-content: center;
  }
  input[type='text'] {
    width: 60%;
    padding: 5px;
    margin-right: 10px;
    color: lightgrey;
  }

  input[type='submit'] {
    margin-left: 10px;
  }

  .footer {
    text-align: right;
    padding-right: 20px;
    font-size: 12px;
    opacity: 60%;
  }
</style>
