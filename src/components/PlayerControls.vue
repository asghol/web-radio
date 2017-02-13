<template>
  <div>
    <button :disabled="!isLoaded" v-on:click="togglePlay();">{{ playbackButtonText }}</button>
    <button :disabled="!isLoaded" v-on:click="stopPlayback();">Stop</button>
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
      playbackButtonText: function () {
        return this.isPlaying ? 'Pause' : 'Play'
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
</style>
