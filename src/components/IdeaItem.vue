<template>
  <div>
    <div class="idea-item" v-bind:style="{'background-color': pickColor}">
      <input type="checkbox" v-on:change="selected"/>
      {{idea.text}}
      <button @click="$emit('del-idea', idea.id)">x</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "IdeaItem",
    props: ["idea"],

    methods: {
      selected() {
        //Modify code missing
        console.log("selected");
      }

    }
  }

  methods: {
    function pickColor() {
      var colors = [
      '#faa4e3', '#ff6b53', '#ff4122', '#92e1df', '#ffb493'
      ];
      var random_color = colors[Math.floor(Math.random() * colors.length)];
      console.log(random_color);
      return random_color;
              
      var x = document.getElementByClass('idea-item');
      x.style.backgroundcolor = random_color;
    } 
  }

</script>

<style scoped>
  .idea-item {
    background: turquoise;
    padding: 16px;
    min-height: 100px;
    width: 100px;
  }
  .is-selected {
    border: groove;
  }

  button {
    background-color: red;
    opacity: 50%;
    border: 0px;
    text-align: center;
  }
</style>