<template>
  <div id="app">
    <NavBar/>
    <AdaptativeFormVue/>
  </div>
</template>

<script>
import AdaptativeFormVue from './components/AdaptativeForm.vue'
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    AdaptativeFormVue,
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
}
</style>
