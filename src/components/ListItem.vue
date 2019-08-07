<template lang="html">
<li>{{country.name}}</li>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
