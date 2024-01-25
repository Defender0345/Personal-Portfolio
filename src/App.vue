<script setup>
import NavBarComp from './components/NavBarComp.vue'
import FooterComp from './components/FooterComp.vue'
</script>

<template>
  <NavBarComp />
  <router-view></router-view>
  <FooterComp />
</template>

<style lang="scss">
@import '@/assets/_shared.scss';

* {
  margin: 0;
  padding: 0;
}
html {
  scroll-behavior: smooth;
}
</style>
