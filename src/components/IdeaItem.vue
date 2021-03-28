<template>
    <div>
      <span :style="pickColor">
      {{idea.text}}
      <div class="buttons">
        <button @click="$emit('show-event', true, false)">Edit</button>
        <button @click="$emit('del-idea', idea.id)">x</button>
      </div>
      </span>
    </div>
</template>

<script>
  export default {
    name: "IdeaItem",
    props: ["idea", 'color'],
    showEdit: false,

    computed: {
      pickColor() {
        var colors = [
        "#faa4e3", "#ff6b53", "#ff4122", "#92e1df", "#ffb493"
        ];
        var random_color = colors[Math.floor(Math.random() * colors.length)];
        //console.log(random_color);
        return {'--color': random_color}
      } 
    }
  }

</script>

<style scoped>
  span {
    background-color: var(--color);
    display: block;
    min-height: 100px;
    width: 100px;
    padding: 16px;
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
    opacity: 50%;
    border: 0px;
    text-align: center;
    margin: 3px;
  }
  button:hover {
    opacity: 90%;
    color: black;
    box-shadow: 2px 1px grey;
  }
</style>