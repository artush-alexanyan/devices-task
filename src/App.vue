<template>
  <div id="app">
    <AppNavbar />
    <Rewards />
  </div>
</template>

<script>
import Rewards from './components/Rewards.vue'
import AppNavbar from './app-components/AppNavbar'

export default {
  name: 'App',
  components: {
    Rewards,
    AppNavbar
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
