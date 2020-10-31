<template>
  <div id="app">
    <CatRandom/>
  </div>
</template>

<script>
import CatRandom from './components/CatRandom.vue'

export default {
  name: 'App',
  components: {
    CatRandom
  }
}
</script>

<style>
#app {
  box-sizing: border-box;
  margin: 0 auto;
}
</style>
