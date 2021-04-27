<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Interceptor/>
  </div>
</template>

<script>
import Interceptor from './components/Interceptor.vue'

export default {
  name: 'App',
  components: {
    Interceptor
  }
}
</script>