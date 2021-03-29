<template>
    <div>
        <div v-bind:key="comment.id" v-for="comment in comments">
            <CommentItem v-bind:comment="comment"/>
        </div>
    </div> 
</template>

<script>
    import CommentItem from './CommentItem.vue';

    export default {
        name: Comments,
        components: {
            CommentItem
        },

        props: ["idea","comments"]
    }
</script>

<style scoped>

</style>