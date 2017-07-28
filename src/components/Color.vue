<template>
<div class="color">
  <div class="swatch" :style="{ backgroundColor: '#' + hex }"></div>
  {{ name }}<br>
  ({{ rgb.r }}, {{ rgb.g }}, {{rgb.b}})<br>
  {{ cleanHex }}
</div>
</template>

<script>
export default {
  name: 'color',
  props: [ 'hex' ],
  data () {
    return {
      name: '-',
      rgb: {r: null, g: null, b: null},
      cleanHex: this.hex
    }
  },
  created () {
    this.getColorData()
  },
  methods: {
    getColorData: function () {
      let vm = this
      axios.get('http://www.thecolorapi.com/id?hex=' + vm.hex, {timeout: 5000})
        .then(function (response) {
          vm.name = response.data.name.value
          vm.rgb = response.data.rgb
          vm.cleanHex = response.data.hex.value
        })
        .catch(function (error) {
          console.log(error)
          //TODO: fallback -> local conversion to rgb, placeholder name
          vm.name = '[[ no name found ]]'
        })
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
