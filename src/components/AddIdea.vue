<template>
  <div>
    <form v-on:submit="addIdea">
      <input type="text" v-model="text" name="text" placeholder="Type your new idea here!" />
      <input type="submit" value="Submit" class="btn"/>
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
          text: this.text
        }
        this.$emit('add-idea', newIdea);
        this.text ='';
      }
    }
  }

</script>

<style scoped>
form{
  display: flex;
  padding-left: 20px;
  padding-right: 20px;
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>