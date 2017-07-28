<template>
<div id="colors">
  <color v-for="color in colors" :hex="color.hex"></color>
</div>
</template>

<script>
import Color from './Color.vue'

export default {
  name: 'color-list',
  components: { Color },
  data () {
    return { colors: [
        { hex: '#123132' },
        { hex: '#916df4' }
    ]}
  }
}
</script>

<style lang="stylus" scoped>
</style>
