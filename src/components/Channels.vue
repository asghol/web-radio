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
  ul {
    display: flex;
    flex-wrap: wrap;
  }
  li {
    flex: 1 1 auto;
    list-style: none;
    width: 140px;
  }
</style>
