<template>
  <div>
    <label>Package</label>
    <select name="packages" v-on:change="packageSelected($event);">
      <option v-for="(channelPackage, index) in packages"
              :selected="channelPackage.name === selectedPackage.name"
              :value="channelPackage.name">
              {{channelPackage.name}}
      </option>
    </select>
  </div>
</template>

<script>
  export default {
    name: 'package-selector',
    props: [ 'packages', 'selectedPackage' ],
    methods: {
      packageSelected (event) {
        for (var channelPackage in this.packages) {
          if (this.packages[channelPackage].name === event.target.value) {
            return this.$emit('packageSelected', this.packages[channelPackage])
          }
        }
      }
    }
  }
</script>
