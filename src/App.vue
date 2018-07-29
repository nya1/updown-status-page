<template>
  <div id="app">
    <StatusPage/>
  </div>
</template>

<script>
import StatusPage from './components/StatusPage'

export default {
  name: 'App',
  components: {
    StatusPage
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
