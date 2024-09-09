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

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  background-color: #f5f5f5; /* เพิ่มสีพื้นหลังให้ดูสะอาดตา */
  min-height: 100vh; /* ให้แน่ใจว่าพื้นที่ของแอพเต็มความสูงของหน้าจอ */
}

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
