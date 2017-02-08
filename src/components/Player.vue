<template>
  <audio id="player" :src="playbackUrl" controls autoplay
          v-on:loadeddata="loaded($event);"
          v-on:playing="playing($event);">
  </audio>
</template>

<script>
  export default {
    name: 'player',
    props: [ 'currentChannel', 'qualitySelected', 'isPlaying' ],
    computed: {
      playbackUrl: function () {
        if (this.currentChannel.url != null) {
          return this.currentChannel.url[this.qualitySelected]
        }
        return ''
      }
    },
    watch: {
      isPlaying: function (val) {
        if (val === true) {
          document.getElementById('player').play()
        } else {
          document.getElementById('player').pause()
        }
      }
    },
    methods: {
      loaded: function () {
        this.$emit('loaded')
      },
      playing: function (event) {
        this.$emit('playing')
      }
    }
  }
</script>

<style scoped>
  audio {
    display: none;
  }
</style>
