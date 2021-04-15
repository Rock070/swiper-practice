<template>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup () {
    const classmates = {
      rock: {
        age: 23,
        color: 'blue',
      },
      alysa: {
        age: 23,
        color: 'green',
      }
    }
    console.log(classmates?.john ?? "no that guy")

    if(!classmates.john) {
      console.log('no that guy')
    }

    return {
      classmates,
    }
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
