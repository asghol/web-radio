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
  ul {
    margin: 0;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
  }
  li {
    flex: 1 1 auto;
    list-style: none;
    width: 10em;
  }
  img {
    height: 5em;
  }

  @media (min-width: 320px) {
    ul {
      margin: 0 0 0 2.6em;
    }
    li {
      width: 8.2em;
    }
    img {
      height: 3em;
    }
  }
</style>
