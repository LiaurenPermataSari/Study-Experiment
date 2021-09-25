<template>
  <div class="app">
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
}
</script>

<style>
.app {
  justify-content: center;
  padding: 310px;
  background-image: #D4ECDD;
}
</style>