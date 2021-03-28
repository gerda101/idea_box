<template>
    <div>
      <span :style="pickColor">
      <input type="checkbox" v-on:change="selected"/>
      {{idea.text}}
      <button class="del_button" @click="$emit('del-idea', idea.id)">x</button>
      </span>
    </div>
</template>

<script>
  export default {
    name: "IdeaItem",
    props: ["idea", 'color'],

    computed: {
      pickColor() {
        var colors = [
        "#faa4e3", "#ff6b53", "#ff4122", "#92e1df", "#ffb493"
        ];
        var random_color = colors[Math.floor(Math.random() * colors.length)];
        console.log(random_color);
        return {'--color': random_color}
      } 
    },

    methods: {
      selected() {
        //Modify code missing
        console.log("selected");
      },
    }
  }

</script>

<style>
  span {
    background-color: var(--color);
    display: block;
    min-height: 100px;
    width: 100px;
    padding: 16px;
  }

  .del_button {
    background-color: red;
    opacity: 70%;
    border: 0px;
    text-align: center;
  }
</style>