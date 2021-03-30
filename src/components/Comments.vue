<template>
    <div class="flexreference">
        <div v-bind:key="comment.id" v-for="comment in comments">
            <div v-if="comment.idea_id==idea.id">
                <span class="comments">
                    <p><CommentItem v-bind:comment="comment" @del-comment="$emit('del-comment', comment.id)" /></p>
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
        align-items: flex-end;
    }
    p {
    font-family: 'Abril Fatface', serif;
    text-align:justify;
    font-size: 1.2vw;
    padding: 5px;
    margin: 1px;
    }
    .comments {
        background-color: whitesmoke;
        display: block;
        min-height: 5px;
        width: 160px;
        padding: 5px;
    }
</style>