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
import QualitySelection from './components/QualitySelection'
import Player from './components/Player'
import PlayerControls from './components/PlayerControls'

export default {
  name: 'app',
  components: {
    Channels,
    QualitySelection,
    Player,
    PlayerControls
  },
  data () {
    return {
      channelList: [
        {
          name: 'P4',
          image: '/static/img/p4.png',
          url: {
            0: 'http://stream.p4.no/p4_aac_lq',
            1: 'http://stream.p4.no/p4_aac_mq',
            2: 'http://stream.p4.no/p4_mp3_hq'
          }
        },
        {
          name: 'P5 Hits',
          image: '/static/img/p5hits.png',
          url: {
            0: 'http://stream.p4.no/p5oslo_aac_lq',
            1: 'http://stream.p4.no/p5oslo_aac_mq',
            2: 'http://stream.p4.no/p5oslo_mp3_hq'
          }
        },
        {
          name: 'P5 Hits Bergen',
          image: '/static/img/p5hitsbergen.png',
          url: {
            0: 'http://stream.p4.no/p5bergen_aac_lq',
            1: 'http://stream.p4.no/p5bergen_aac_mq',
            2: 'http://stream.p4.no/p5bergen_mp3_hq'
          }
        },
        {
          name: 'P6 Rock',
          image: '/static/img/p6rock.png',
          url: {
            0: 'http://stream.p4.no/p6_aac_lq',
            1: 'http://stream.p4.no/p6_aac_mq',
            2: 'http://stream.p4.no/p6_mp3_hq'
          }
        },
        {
          name: 'P7 Klem',
          image: '/static/img/p7klem.png',
          url: {
            0: 'http://stream.p4.no/p7_aac_lq',
            1: 'http://stream.p4.no/p7_aac_mq',
            2: 'http://stream.p4.no/p7_mp3_hq'
          }
        },
        {
          name: 'NRJ',
          image: '/static/img/nrj.png',
          url: {
            0: 'http://stream.p4.no/nrj_aac_lq',
            1: 'http://stream.p4.no/nrj_aac_mq',
            2: 'http://stream.p4.no/nrj_mp3_hq'
          }
        },
        {
          name: 'P8 Pop',
          image: '/static/img/p8pop.png',
          url: {
            0: 'http://stream.p4.no/p8_aac_lq',
            1: 'http://stream.p4.no/p8_aac_mq',
            2: 'http://stream.p4.no/p8_mp3_hq'
          }
        },
        {
          name: 'P9 Retro',
          image: '/static/img/p9retro.png',
          url: {
            0: 'http://stream.p4.no/p9_aac_lq',
            1: 'http://stream.p4.no/p9_aac_mq',
            2: 'http://stream.p4.no/p9_mp3_hq'
          }
        },
        {
          name: 'P10 Country',
          image: '/static/img/p10country.png',
          url: {
            0: 'http://stream.p4.no/p10_aac_lq',
            1: 'http://stream.p4.no/p10_aac_mq',
            2: 'http://stream.p4.no/p10_mp3_hq'
          }
        },
        {
          name: 'Bandit',
          image: '/static/img/bandit.png',
          url: {
            0: 'http://stream.p4.no/bandit_aac_lq',
            1: 'http://stream.p4.no/bandit_aac_mq',
            2: 'http://stream.p4.no/bandit_mp3_hq'
          }
        },
        {
          name: 'P5 Nonstop Hits',
          image: '/static/img/p5nonstophits.png',
          url: {
            0: 'http://stream.p4.no/p5nonstophits_aac_lq',
            1: 'http://stream.p4.no/p5nonstophits_aac_mq',
            2: 'http://stream.p4.no/p5nonstophits_mp3_hq'
          }
        },
        {
          name: 'P5 Hits Trondheim',
          image: '/static/img/p5hitstrondheim.png',
          url: {
            0: 'http://stream.p4.no/p5trondheim_aac_lq',
            1: 'http://stream.p4.no/p5trondheim_aac_mq',
            2: 'http://stream.p4.no/p5trondheim_mp3_hq'
          }
        },
        {
          name: 'P5 Hits Stavanger',
          image: '/static/img/p5hitsstavanger.png',
          url: {
            0: 'http://stream.p4.no/p5stavanger_aac_lq',
            1: 'http://stream.p4.no/p5stavanger_aac_mq',
            2: 'http://stream.p4.no/p5stavanger_mp3_hq'
          }
        }
      ],
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
      qualitySelected: 0,
      isLoaded: false,
      isPlaying: false
    }
  },
  methods: {
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
