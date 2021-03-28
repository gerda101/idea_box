<template>
    <div>
    <form v-on:submit="addIdea">
      <input type="text" v-model="text" name="text" />
      <input type="submit" value="Confirm datachange" class="btn" />
    </form>
    </div>
</template>

<script>
export default {
    name: "EditIdea",
    data(){
      return {
        text: ''
      }
    },
    methods: {
      editIdea(e) {
        e.preventDefault();
        this.showEdit = true;
        this.showNew = false;
        oldId = this.id;
        const editedIdea = {
          id: uuid.v4(),
          text: this.text
        }
        this.$emit('add-idea', oldId, editedIdea);
        this.text ='';
      }
    }
}
</script>

<style scoped>

</style>
