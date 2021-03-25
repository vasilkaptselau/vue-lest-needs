<template>
  <img alt="Vue logo" src="./assets/my_logo.png">
  <TableCards msg="Welcome to Your Vue.js App"/>

</template>

<script>
import TableCards from './components/TableCards.vue'

export default {
  name: 'App',
  components: {
    TableCards
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
