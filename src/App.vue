<template>
  <div id="app" class="app">
    <Header/>
    <AddIdea v-on:add-idea='addIdea'/>
    <Ideas v-bind:ideas="ideas" v-on:del-idea="deleteIdea" @update-idea="saveUpdatedIdea"/>
    <p class="footer">Made by Gerda Urbán in 2021</p>
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
      AddIdea,
    },

    data() {
      return {
        ideas: [
          {
            id: 1,
            text: "Test idea 1",
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
      saveUpdatedIdea(editedIdea){
        this.ideas.forEach(idea => {
          if(this.idea.id == editedIdea.id){
            this.idea.text = editedIdea.text;
          }
        });
        //Prevent refresh/long-term storage missing
      },
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
    cursor: pointer;
    border: 0px;
    padding-right: 10px;
    padding-left: 10px;
  }
  .btn:hover {
    opacity: 100%;
    box-shadow: 2px 1px grey;
  }

  .buttons {
    position: absolute;
    bottom: 5px;
    align-items: right;
  }
  .button {
    background-color: lightgrey;
    color: grey;
    opacity: 60%;
    border: 0px;
    text-align: center;
    margin: 3px;
  }
  .button:hover {
    opacity: 90%;
    color: black;
    box-shadow: 2px 1px grey;
    cursor: pointer;
  }

  .menu-buttons {
    display: flex;
    flex-direction: column;
    opacity: 100%;
    align-items: flex-end;
    align-self: flex-end;
    margin: 5px;
  }

  form{
    display: flex;
    flex-direction: column;
    margin: 5px;
    align-items: right;
  }
  input[type='text'] {
    padding: 5px;
    margin: 5px;
    color: grey;
  }

  textarea {
    border: 0px;
    margin-right: 10px;
    margin-top: 5px;
    align-self: flex-end;
    padding: 10px;
    width: 70%;
    word-wrap: normal;
    min-height: 100px;
    resize: unset;
  }

  .footer {
    text-align: right;
    padding-right: 20px;
    font-size: 12px;
    opacity: 60%;
  }
</style>
