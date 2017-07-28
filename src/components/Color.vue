<template>
<div class="color">
  <div class="swatch" :style="{ backgroundColor: cleanHex }"></div>
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
      cleanHex: '#' + this.hex
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
          vm.rgb = {r: response.data.rgb.r, g: response.data.rgb.g, b: response.data.rgb.b}
          vm.cleanHex = response.data.hex.value
        })
        .catch(function (error) {
          console.log(error)
          vm.name = '[[ no name found ]]'
          vm.rgb = {
            r: parseInt(vm.hex.substr(0,2), 16),
            g: parseInt(vm.hex.substr(2,2), 16),
            b: parseInt(vm.hex.substr(4,2), 16)
          }
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
