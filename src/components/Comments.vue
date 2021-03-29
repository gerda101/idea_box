<template>
    <div class="flexreference">
        <div v-bind:key="comment.id" v-for="comment in comments">
            <div v-if="comment.idea_id==idea.id">
                <span class="comments">
                    <CommentItem v-bind:comment="comment" @del-comment="$emit('del-comment', comment.id)" />
                </span>
            </div>
        </div>
    </div> 
</template>

<script>
    import CommentItem from './CommentItem';

    export default {
        name: "Comments",

        components: {
            CommentItem
        },

        props: ["comments", "idea"]
    }
</script>

<style scoped>
    .flexreference {
        display: flex;
        position: relative;
        flex-wrap: wrap;
        flex-direction: column-reverse;
    }
    .comments {
        background-color: whitesmoke;
        display: inline-block;
        min-height: 5px;
        width: 160px;
        padding: 12px;
    }
</style>