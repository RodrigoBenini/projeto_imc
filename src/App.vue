<script setup>
import BmiCalculator from './components/BmiCalculator.vue';
import Header from './components/Header.vue';
</script>

<template>
  <div id="app">
    <Header></Header>
    <BmiCalculator></BmiCalculator>
  </div>
</template>

<style>
body {
  background: url(assets/healthy.jpg) no-repeat center fixed;
  background-size: cover;
  height: 100%;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html,* {
  font-family: 'Ribeye Marrow', cursive;
  margin:0 0 ;
}
</style>