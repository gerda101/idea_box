<template>
    <div class="comment">
        {{comment.comment_text}}
        <button class="button" @click="$emit('del-comment', comment.id)">x</button>
    </div>
</template>

<script>
    export default {
        name: "CommentItem",
        props: ["comment"]
    }
</script>

<style scoped>
    .comment {
        border: dotted;
        border-color: grey;
        border-width: 1px;
        padding: 5px;
        padding-left: 15px;
        position: relative;
    }
</style>