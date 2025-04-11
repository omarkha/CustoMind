<template>
  <NavBar />
  <HomePage />
  <FooterComp />
</template>

<script setup>
import NavBar from "./components/NavBar.vue";
import HomePage from "./components/public/HomePage.vue";
import FooterComp from "./components/FooterComp.vue";
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
