<template>
    <div>
      <span :style="pickColor">
        <div class="idea" v-show="!editing">
          {{idea.text}}
          <button @click="viewComments = true">Show comments</button>
          <div v-show="viewComments & !editing">
            <Comments v-bind:comment="comment"/>
          </div>
          <div class="buttons" v-show="!editing & !commenting">
            <button @click="commenting = true">Com</button>
            <button @click="editing = true">Edit</button>
            <button @click="$emit('del-idea', idea.id)">x</button>
          </div>
        </div>

      <div class="editform" v-show="editing">
        <form v-on:submit="updateIdea, editing=false">
          <input type="text" v-model="idea.text" name="updateText" />
          <div class="menu-buttons">
            <input type="submit" class="menu-button" value="Confirm datachange"/>
            <input type="button" class="menu-button" @click="editing = false" value="Back"/>
          </div>
        </form>
      </div>

      <div class="comment" v-show="commenting">
        <form v-on:submit="newComment, commenting=false">
          <textarea name="comment" placeholder="Type your opinion about this idea here!" />
          <div class="menu-buttons">
            <input type="submit" class="menu-button" value="Add comment"/>
            <input type="button" class="menu-button" @click="commenting = false" value="Back"/>
          </div>
        </form>
      </div>

      </span>
    </div>
</template>

<script>
  import Comments from './Comments.vue'

  export default {
    name: "IdeaItem",
    props: ["idea", 'color', "comments"],
    showEdit: false,

    components: {
      Comments
    },

    data() {
      return{
        editing: false,
        commenting: false,
        viewComments: false,
        
        comments: [
          {
            id: 1,
            idea_id: 1,
            comment_text: "Teszt comment"
          }
        ]
      }
    },

    computed: {
      pickColor() {
        var colors = [
        "#faa4e3", "#ff6b53", "#ff4122", "#92e1df", "#ffb493"
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
    }
  }

</script>

<style scoped>
  .idea {
    padding: 5px;
    font-size: 18px;
  }
  span {
    background-color: var(--color);
    display: block;
    min-height: 150px;
    width: 150px;
    padding: 16px;
    padding-bottom: 30px;
    position: relative;
  }

  .buttons {
    position: absolute;
    bottom: 10px;
    right: 10px;
  }
  button {
    background-color: lightgrey;
    color: lightgrey;
    opacity: 60%;
    border: 0px;
    text-align: center;
    margin: 3px;
  }
  button:hover {
    opacity: 90%;
    color: black;
    box-shadow: 2px 1px grey;
    cursor: pointer;
  }

  form{
    display: flex;
    flex-direction: column;
    margin: 5px;
    align-items: right;
  }
  input[type='text'] {
    padding: 5px;
    margin: 5px;
    color: grey;
  }

  .comment {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  textarea {
    border: 0px;
    padding: 10px;
    width: 80%;
    word-wrap: normal;
    min-height: 100px;
    resize: unset;
  }

  .menu-buttons {
    display: flex;
    flex-direction: column;
    opacity: 100%;
    align-items: flex-end;
    align-self: flex-end;
    margin: 5px;
  }
  .menu-button {
    margin: 5px;
    padding: 5px;
    background: #eb9b45;
    cursor: pointer;
    border: 0px;
    text-align: center;
    width: fit-content;
    opacity: 80%;
  }
  .menu-button:hover {
    opacity: 100%;
    box-shadow: 2px 1px grey;
  }
</style>