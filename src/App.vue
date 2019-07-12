<template>
  <div id="app">
    Calendario de comida semanal
    <CalendarioComida msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import CalendarioComida from './components/CalendarioComida.vue'

export default {
  name: 'app',
  components: {
    CalendarioComida
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
