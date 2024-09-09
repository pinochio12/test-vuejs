<template>
  <div id="app">
    <TestComponent />
  </div>
</template>

<script>
import TestComponent from './components/test1.vue';

export default {
  name: 'App',
  components: {
    TestComponent
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
