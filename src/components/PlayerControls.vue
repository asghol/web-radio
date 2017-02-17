<template>
  <div>
    <figure>
      <button :class="playbackButtonClass" :disabled="!isLoaded" v-on:click="togglePlay();"></button>
    </figure>
    <figure>
      <button class="stop" :disabled="!isLoaded" v-on:click="stopPlayback();"></button>
    </figure>
  </div>
</template>

<script>
  export default {
    name: 'player-controls',
    props: ['currentChannel', 'isPlaying', 'isLoaded'],
    data: function () {
      return {
        disabled: true
      }
    },
    computed: {
      playbackButtonClass: function () {
        return this.isPlaying ? 'pause' : 'play'
      }
    },
    methods: {
      togglePlay: function () {
        this.$emit('play', !this.isPlaying)
      },
      stopPlayback: function () {
        this.$emit('stop')
      }
    }
  }
</script>

<style scoped>
  div {
    display: inline-flex;
  }

  figure button {
    width: 50px;
    height: 50px;
    background: red;
    border: none;
    border-radius: 100%;
    margin: auto;
    cursor: pointer;
  }

  figure button:disabled {
    background: grey;
  }

  figure button:focus {
    outline: 0;
    border: 1px solid hsl(210, 58%, 69%);
    box-shadow: 0 0 0 3px hsla(210, 76%, 57%, 0.5);
  }

  figure button.play::after {
    content: '';
    display: inline-block;
    position: relative;
    top: 1px;
    left: 3px;
    border-style: solid;
    border-width: 10px 0 10px 20px;
    border-color: transparent transparent transparent white;
  }

  figure button.stop::after {
    content: '';
    display: inline-block;
    position: relative;
    top: 1px;
    border-style: solid;
    border-width: 0 10px 20px 10px;
    border-color: white;
  }

  figure button.pause::after {
    content: '';
    display: inline-block;
    position: relative;
    top: 1px;
    width: 7px;
    height: 20px;
    border-left: 6px solid white;
    border-right: 6px solid white;
  }
</style>
