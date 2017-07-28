<template>
<div class="color">
  <div class="swatch" :style="{ backgroundColor: '#' + hex }"></div>
  {{ name }}<br>
  ()<br>
  #{{ hex }}
</div>
</template>

<script>
export default {
  name: 'color',
  props: [ 'hex' ],
  data () {
    return { name: this.getColorData(this.hex) }
  },
  methods: {
    getColorData: function (hex) {
      axios.get('http://thecolorapi.com/id?hex=' + hex)
        .then(function (response) {
          console.log(response)
          return response.name.value
        })
        .catch(function (error) {
          console.log("ERROR")
          return null
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
