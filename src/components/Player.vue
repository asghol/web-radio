<template>
  <audio id="player" :src="playbackUrl" controls autoplay></audio>
</template>

<script>
  export default {
    name: 'player',
    props: [ 'currentChannel', 'qualitySelected' ],
    computed: {
      playbackUrl: function () {
        if (this.currentChannel.url != null) {
          return this.currentChannel.url[this.qualitySelected]
        }
        return ''
      }
    }
  }
</script>
