<template>
<div id="app">
  <h1>Colors</h1>
  <color-list></color-list>
  <!-- <add-button></add-button> -->
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
h1
  font-size 1rem
  font-weight bold
  font-family sans-serif
</style>
