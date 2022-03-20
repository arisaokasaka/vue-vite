<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Content from './components/Content.vue';
import Spacer from './components/Spacer.vue';
</script>

<template>
  <Header />
  <Spacer :top="40" />
  <Content />
  <Spacer :top="60" />
  <Footer />
</template>

<style>
html,
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding-top: 54px; /* headerが54px */
}
</style>
