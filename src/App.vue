<template>
  <div id="app">
    <player :currentChannel=currentChannel
            :qualitySelected=qualitySelected
            :isPlaying=isPlaying
            v-on:playing="playing"
            v-on:loaded="loaded">
    </player>
    <player-controls  :currentChannel=currentChannel
                      :isPlaying=isPlaying
                      :isLoaded=isLoaded
                      v-on:play="play"
                      v-on:stop="stop">
    </player-controls>
    <package-selector :packages=packages
                      :selectedPackage=selectedPackage
                      v-on:packageSelected="packageSelected">
    </package-selector>
    <quality-selection  :qualitySettings=qualityList
                        :selectedQuality=qualitySelected
                        v-on:qualityChanged="qualityChanged">
    </quality-selection>
    <channels :channelList=channelList
              :currentChannel=currentChannel
              v-on:channelSelected="channelSelected">
    </channels>
  </div>
</template>

<script>
import Channels from './components/Channels'
import PackageSelector from './components/PackageSelector'
import QualitySelection from './components/QualitySelection'
import Player from './components/Player'
import PlayerControls from './components/PlayerControls'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    Channels,
    PackageSelector,
    QualitySelection,
    Player,
    PlayerControls
  },
  mounted: function () {
    this.getChannelPacakges()
  },
  data () {
    return {
      channelList: [],
      qualityList: [
        {
          name: 'High',
          qualityIndex: 2
        },
        {
          name: 'Medium',
          qualityIndex: 1
        },
        {
          name: 'Low',
          qualityIndex: 0
        }
      ],
      currentChannel: {},
      selectedPackage: null,
      packages: [],
      qualitySelected: 0,
      isLoaded: false,
      isPlaying: false
    }
  },
  methods: {
    packageSelected (channelPackage) {
      this.selectedPackage = channelPackage
      this.channelList = this.selectedPackage.channelList
    },
    channelSelected (channel) {
      this.currentChannel = channel[0]
    },
    qualityChanged (qualityIndex) {
      this.qualitySelected = qualityIndex
    },
    playing () {
      this.isPlaying = true
    },
    loaded () {
      this.isLoaded = true
    },
    play (playbackToggle) {
      this.isPlaying = playbackToggle
    },
    stop () {
      this.isLoaded = false
      this.isPlaying = false
      this.currentChannel = {}
    },

    getChannelPacakges () {
      var _this = this
      axios.get('/static/channels.json')
        .then(payload => {
          _this.packages = payload.data.packages
          if (_this.selectedPackage === null) {
            _this.selectedPackage = _this.packages[0]
          }
          _this.channelList = _this.selectedPackage.channelList
        })
        .catch(error => {
          console.log(error)
        })
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
