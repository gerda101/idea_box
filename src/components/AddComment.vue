<template>
  <div>
    <form v-on:submit="addComment, $emit('commenting-done')">
        <textarea name="commentInput" placeholder="Type your opinion about this idea here!" />
        <div class="menu-buttons">
          <input type="submit" class="button" value="Add comment"/>
          <input type="button" class="button" @click="$emit('commenting-done')" value="Back"/>
        </div>
    </form>
  </div>
</template>

<script>
import {uuid} from 'vue-uuid';
  export default {
    name: "AddComment",
    
    methods: {
      addComment(e){
        e.prevetDefault();
        const newComment = {
          id: uuid.v4(),
          idea_id: this.idea.id,
          comment: this.commentInput,
        }
        this.$emit(add-comment, newComment);
      },
    }
  }

</script>

<style scoped>
  form {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
</style>