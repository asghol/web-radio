<template>
  <div>
    <label>Quality</label>
    <select name="quality" v-on:change="qualitySelected($event);">
      <option v-for="(quality, index) in getQualityOptions"
              :selected="quality.qualityIndex == selectedQuality"
              :value="quality.qualityIndex">
              {{quality.name}}
      </option>
    </select>
  </div>
</template>

<script>
  export default {
    name: 'quality-selection',
    props: [ 'selectedPackage', 'selectedQuality' ],
    computed: {
      getQualityOptions: function () {
        if (this.selectedPackage) {
          return this.selectedPackage.qualityOptions
        }
        return null
      }
    },
    methods: {
      qualitySelected (event) {
        this.$emit('qualityChanged', event.target.value)
      }
    }
  }
</script>
