<template>
    <div>
      <span :style="pickColor">
        <div v-show="!editing">
          <p>{{idea.text}}</p>
          <div v-show="viewComments & !editing">
            <Comments v-bind:comments="comment_array" v-bind:idea="idea" @del-comment="deleteComment"/>
              <div v-show="commenting">
                <AddComment v-on:add-comment='addComment' @commenting-done="commenting=false"/>
              </div>
          </div>
          <div class="buttons" v-show="!editing & !commenting">
            <button class="button" @click="viewComments = true" v-show="!viewComments">Comments</button>
            <button class="button" @click="viewComments = false" v-show="viewComments">Back</button>
            <button class="button" @click="commenting = true" v-show="viewComments">New Comment</button>
            <button class="button" @click="editing = true" v-show="!viewComments">Edit</button>
            <button class="button" @click="$emit('del-idea', idea.id)" v-show="!viewComments">x</button>
          </div>
        </div>

      <div class="editform" v-show="editing">
        <form v-on:submit="updateIdea, editing=false">
          <input type="text" v-model="idea.text" name="updateText" />
          <div class="menu-buttons">
            <input type="submit" class="button" value="Confirm datachange"/>
            <input type="button" class="button" @click="editing = false" value="Back"/>
          </div>
        </form>
      </div>
      </span>
    </div>
</template>

<script>
  import Comments from './Comments.vue';
  import AddComment from './AddComment';

  export default {
    name: "IdeaItem",
    props: ["idea", 'color', "comments"],
    showEdit: false,

    components: {
      Comments,
      AddComment
    },

    data() {
      return{
        editing: false,
        commenting: false,
        viewComments: false,

        comment_array: [
          {
            id: 1,
            idea_id: 1,
            comment_text: "The page should be reactive too, so it changes according to the window size."
          },
          {
            id: 2,
            idea_id: 3,
            comment_text: "The comments button was pressed, so now you can see them!"
          },
          {
            id: 3,
            idea_id: 3,
            comment_text: "This comment was added later than the one below it."
          }
        ]
      }
    },

    computed: {
      pickColor() {
        var colors = [
        "#faa4e3", "#ff6b53", "#ff4122", "#92e1df", "#ffb493", "#eb9b45", "#e3701d", "#eb9c4a"
        ];
        var random_color = colors[Math.floor(Math.random() * colors.length)];
        //console.log(random_color);
        return {'--color': random_color}
      }
    },

    methods: {
      updateIdea(id, text, e){
        e.prevetDefault();
        const editedIdea = {
          id: id,
          text: text,
        }
        this.$emit('update-idea', editedIdea);
      },
      deleteComment(id) {
        this.comment_array = this.comment_array.filter(comment => comment.id !== id);
      },
      addComment(newComment){
        this.comment_array = [...this.comment_array, newComment];
        //Prevent refresh/long-term storage missing
      },
    }
  }

</script>

<style scoped>
  p {
    font-family: 'Abril Fatface', serif;
    text-align:justify;
    font-size: 1.6vw;
    padding: 5px;
    margin: 10px;
  }
  span {
    background-color: var(--color);
    display: block;
    min-height: 180px;
    width: 200px;
    padding: 16px;
    padding-bottom: 30px;
    position: relative;

  }
</style>