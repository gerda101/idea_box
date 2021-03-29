<template>
    <div class="comment-board" :style="viewComments">
    </div>
</template>

<script>
    export default {
        name: CommentItem,

        props: ["idea","comments"]

    }
</script>

<style scoped>

</style>
