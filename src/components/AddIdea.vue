<template>
  <div class="app">
    <form v-on:submit="addIdea">
      <input type="text" v-model="text" name="text" placeholder="Type your new idea here!" />
      <input type="submit" value="Add new idea to the board!" class="btn"/>
    </form>
  </div>
</template>

<script>
import {uuid} from 'vue-uuid';
  export default {
    name: "AddIdea",
    data(){
      return {
        text: ''
      }
    },
    
    methods: {
      addIdea(e) {
        e.preventDefault();
        const newIdea = {
          id: uuid.v4(),
          text: this.text,
        }
        this.$emit('add-idea', newIdea);
        this.text ='';
      }
    }
  }

</script>

<style scoped>
  .app {
    border: 0px;
  }
  form {
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  input[type='text'] {
    width: 70%;
    padding: 5px;
    margin-right: 10px;
    color: lightgrey;
  }

  input[type='submit'] {
    margin-left: 10px;
  }
</style>