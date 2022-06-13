<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <FormSubmit msg="Submit Form"/>
  </div>
</template>

<script>
import FormSubmit from './components/FormSubmit.vue'

export default {
  name: 'App',
  components: {
    FormSubmit
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
