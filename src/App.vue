<template>
  <navigation/>
</template>

<script>
import navigation from './components/navigation/index.vue'

const name = 'App'
const components = { navigation }
const exposed = { name, components }
export default exposed
</script>
