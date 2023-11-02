<template>
  <div v-on:click="countClicks">
    <h2>
      {{ foodName }}
      <img src="./../assets/vue.svg" v-show="isFavorite" alt="img">
    </h2>
    <p>{{ foodDesc }}</p>
    <button v-on:click="toggleFavorite">Favorite</button>
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
        default: 'This is a default description.',
        validator: function(value) {
          return 2 < value.length && value.length < 3;
        }
      },
      isFavorite: {
        type: Boolean,
        required: false,
        default: false
      }
    },
    emits: ['toggle-favorite'],
    methods: {
      countClicks() {
        this.clicks++;
        },
      toggleFavorite() {
        this.$emit('toggle-Favorite', this.foodName);
      },
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