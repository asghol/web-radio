<template>
  <select name="quality">
    <option v-for="(quality, index) in qualitySettings" :value="quality.qualityIndex">{{quality.name}}</option>
  </select>
</template>

<script>
  export default {
    name: 'quality-selection',
    props: [ 'qualitySettings' ]
  }
</script>
