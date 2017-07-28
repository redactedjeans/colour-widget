<template>
<div id="app">
  <column></column>
  <column></column>
  <column></column>
</div>
</template>

<script>
import Column from './components/Column.vue'

export default {
  name: 'app',
  components: { Column }
}
</script>

<style lang="stylus">
body
  margin 0
  font-size 62.5%
  min-width 320px
</style>
