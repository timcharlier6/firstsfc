<template>
  <div v-on:click="countClicks">
    <h2>
      {{ foodName }}
      <img src="./../assets/vue.svg" v-show="isFavorite" alt="img">
    </h2>
    <p>{{ foodDesc }}</p>
    <p id="red">Number of clicks : {{ clicks }}</p>
  </div>
</template>

<script>
  export default {

    data() {
      return {
        clicks: 0
      }
    },
    // props: ['foodName','foodDesc','isFavorite']
    props: {
      foodName: {
        type: String,
        required: true
      },
      foodDesc: {
        type: String,
        required: false,
        default: 'This is a default description.'
      },
      isFavorite: {
        type: Boolean,
        required: false,
        default: false
      }
    },
    methods: {
      countClicks() {
        this.clicks++;
      }
    }
  }
</script>

<style>
  #red {
    font-weight: bold ;
    color: rgb(144, 12, 12);
  }

  img {
    height: 1.5em;
    float: right;
  }
</style>