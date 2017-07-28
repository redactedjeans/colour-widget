<template>
<div class="color">
  <div class="swatch" :style="{ backgroundColor: strHex }"></div>
  {{ name }}<br>
  ({{ rgb.r }}, {{ rgb.g }}, {{rgb.b}})<br>
  {{ strHex }}
</div>
</template>

<script>
import ntc from 'ntc'

export default {
  name: 'color',
  props: [ 'hex' ],
  data () {
    return {
      name: '-',
      rgb: {r: null, g: null, b: null},
      strHex: '#' + this.hex
    }
  },
  created () {
    this.getColorData()
  },
  methods: {
    getColorData: function () {
      this.name = ntc.name(this.hex)[1]
      this.rgb = {
        r: parseInt(this.hex.substr(0,2), 16),
        g: parseInt(this.hex.substr(2,2), 16),
        b: parseInt(this.hex.substr(4,2), 16)
      }
      this.strHex = '#' + this.hex.toLowerCase()
    }
  }
}
</script>

<style lang="stylus" scoped>
swatch-size = 2rem

.color
  font-family monospace
  margin-bottom 1rem
  height 2rem
  font-size .75rem

.swatch
  float left
  margin-right 1rem
  height swatch-size
  width swatch-size
</style>
