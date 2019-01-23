<template>
  <div id="app">
    <Hi msg="我是来自APP的msg"/>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <h1>121212</h1>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Hi from './components/Hi.vue'
export default {
  name: 'app',
  components: {
    HelloWorld,
    Hi
  }
}


</script>

<style scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  h1 {
    color: red;
  }
</style>
