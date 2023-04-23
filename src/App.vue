<template>
  <div id="app">
    <DistributionNumbers />
  </div>
</template>

<script>
import DistributionNumbers from './components/DistributionNumbers.vue'

export default {
  name: 'App',
  components: {
    DistributionNumbers
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
