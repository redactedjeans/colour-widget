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
        { hex: '160004' },
        { hex: 'f7fefe' },
        { hex: '5f021f' },
        { hex: '1f363d' },
        { hex: '40798c' }
    ]}
  }
}
</script>

<style lang="stylus">
</style>
