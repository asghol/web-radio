<template>
  <ul>
    <li v-for="(channel, index) in channelList">
      <img :src="channel.image" v-on:click="channelSelected(channel);"></img>
    </li>
  </ul>
</template>

<script>
  export default {
    name: 'channels',
    props: [ 'channelList', 'currentChannel' ],
    methods: {
      channelSelected (channel) {
        this.$emit('channelSelected', [channel])
      }
    }
  }
</script>

<style scoped>
  img {
    height: 5em;
  }
  li {
    list-style: none;
  }
</style>
