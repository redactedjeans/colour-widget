<template>
<div :style="{ backgroundColor: hex, }">color: {{ hex }}</div>
</template>

<script>
export default {
  name: 'color',
  props: [ 'hex' ],
  data () { return {} }
}
</script>

<style lang="stylus" scoped>
</style>
