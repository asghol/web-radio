<template>
  <ul>
    <li v-for="(channel, index) in channelList">
      <div v-if="channel.image">
        <img :src="channel.image" v-on:click="channelSelected(channel);"></img>
      </div>
      <div v-else>
        <button v-on:click="channelSelected(channel);">{{channel.name}}</button>
      </div>
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
    margin: 1em;
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
    li {
      width: 8.2em;
    }
    img {
      height: 3em;
    }
  }
</style>
