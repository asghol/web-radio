<template>
  <audio :src="currentChannel.url" controls></audio>
</template>

<script>
  export default {
    name: 'player',
    props: [ 'currentChannel' ]
  }
</script>
