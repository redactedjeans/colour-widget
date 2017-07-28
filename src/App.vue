<template>
<div id="app">
  <color-list></color-list>
  <add-button></add-button>
</div>
</template>

<script>
import ColorList from './components/Colors.vue'
import AddButton from './components/AddButton.vue'

export default {
  name: 'app',
  components: {
    ColorList,
    AddButton
  }
}
</script>

<style lang="stylus">
body
  margin 0
  font-size 62.5%
  min-width 320px
</style>
