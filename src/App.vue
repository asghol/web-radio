<template>
  <div id="app">
    <channels :channelList=channelList :currentChannel=currentChannel v-on:channelSelected="channelSelected"></channels>
    <player :currentChannel=currentChannel></player>
  </div>
</template>

<script>
import Channels from './components/Channels'
import Player from './components/Player'

export default {
  name: 'app',
  components: {
    Channels,
    Player
  },
  data () {
    return {
      channelList: [
        {
          name: 'P9 Retro',
          image: '../assets/p9retro.png',
          url: 'http://stream.p4.no/p9_mp3_hq'
        }
      ],
      currentChannel: {}
    }
  },
  methods: {
    channelSelected (channel) {
      this.currentChannel = channel[0]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
