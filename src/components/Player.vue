<template>
  <audio id="player" :src="currentChannel.url" controls autoplay></audio>
</template>

<script>
  export default {
    name: 'player',
    props: [ 'currentChannel' ]
  }
</script>
