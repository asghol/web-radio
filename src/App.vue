<template>
  <div id="app">
    <player :currentChannel=currentChannel :qualitySelected=qualitySelected></player>
    <quality-selection :qualitySettings=qualityList></quality-selection>
    <channels :channelList=channelList :currentChannel=currentChannel v-on:channelSelected="channelSelected"></channels>
  </div>
</template>

<script>
import Channels from './components/Channels'
import QualitySelection from './components/QualitySelection'
import Player from './components/Player'

export default {
  name: 'app',
  components: {
    Channels,
    QualitySelection,
    Player
  },
  data () {
    return {
      channelList: [
        {
          name: 'P4',
          image: '/static/p4.png',
          url: {
            0: 'http://stream.p4.no/p4_aac_lq',
            1: 'http://stream.p4.no/p4_aac_mq',
            2: 'http://stream.p4.no/p4_mp3_hq'
          }
        },
        {
          name: 'P5 Hits',
          image: '/static/p5hits.png',
          url: {
            0: 'http://stream.p4.no/p5oslo_aac_lq',
            1: 'http://stream.p4.no/p5oslo_aac_mq',
            2: 'http://stream.p4.no/p5oslo_mp3_hq'
          }
        },
        {
          name: 'P5 Hits Bergen',
          image: '/static/p5hitsbergen.png',
          url: {
            0: 'http://stream.p4.no/p5bergen_aac_lq',
            1: 'http://stream.p4.no/p5bergen_aac_mq',
            2: 'http://stream.p4.no/p5bergen_mp3_hq'
          }
        },
        {
          name: 'P6 Rock',
          image: '/static/p6rock.png',
          url: {
            0: 'http://stream.p4.no/p6_aac_lq',
            1: 'http://stream.p4.no/p6_aac_mq',
            2: 'http://stream.p4.no/p6_mp3_hq'
          }
        },
        {
          name: 'P7 Klem',
          image: '/static/p7klem.png',
          url: {
            0: 'http://stream.p4.no/p7_aac_lq',
            1: 'http://stream.p4.no/p7_aac_mq',
            2: 'http://stream.p4.no/p7_mp3_hq'
          }
        },
        {
          name: 'NRJ',
          image: '/static/nrj.png',
          url: {
            0: 'http://stream.p4.no/nrj_aac_lq',
            1: 'http://stream.p4.no/nrj_aac_mq',
            2: 'http://stream.p4.no/nrj_mp3_hq'
          }
        },
        {
          name: 'P8 Pop',
          image: '/static/p8pop.png',
          url: {
            0: 'http://stream.p4.no/p8_aac_lq',
            1: 'http://stream.p4.no/p8_aac_mq',
            2: 'http://stream.p4.no/p8_mp3_hq'
          }
        },
        {
          name: 'P9 Retro',
          image: '/static/p9retro.png',
          url: {
            0: 'http://stream.p4.no/p9_aac_lq',
            1: 'http://stream.p4.no/p9_aac_mq',
            2: 'http://stream.p4.no/p9_mp3_hq'
          }
        },
        {
          name: 'P10 Country',
          image: '/static/p10country.png',
          url: {
            0: 'http://stream.p4.no/p10_aac_lq',
            1: 'http://stream.p4.no/p10_aac_mq',
            2: 'http://stream.p4.no/p10_mp3_hq'
          }
        },
        {
          name: 'Bandit',
          image: '/static/bandit.png',
          url: {
            0: 'http://stream.p4.no/bandit_aac_lq',
            1: 'http://stream.p4.no/bandit_aac_mq',
            2: 'http://stream.p4.no/bandit_mp3_hq'
          }
        },
        {
          name: 'P5 Nonstop Hits',
          image: '/static/p5nonstophits.png',
          url: {
            0: 'http://stream.p4.no/p5nonstophits_aac_lq',
            1: 'http://stream.p4.no/p5nonstophits_aac_mq',
            2: 'http://stream.p4.no/p5nonstophits_mp3_hq'
          }
        },
        {
          name: 'P5 Hits Trondheim',
          image: '/static/p5hitstrondheim.png',
          url: {
            0: 'http://stream.p4.no/p5trondheim_aac_lq',
            1: 'http://stream.p4.no/p5trondheim_aac_mq',
            2: 'http://stream.p4.no/p5trondheim_mp3_hq'
          }
        },
        {
          name: 'P5 Hits Stavanger',
          image: '/static/p5hitsstavanger.png',
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
      qualitySelected: 0
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
