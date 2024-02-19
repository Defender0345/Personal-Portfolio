<script setup>
// import NavBarComp from './components/NavBarComp.vue'
import FooterComp from './components/FooterComp.vue'
import SideBarComp from '@/components/SideBarComp.vue'
</script>

<template>
  <div class="main-app">
    <div class="app">
      <SideBarComp />
      <router-view></router-view>
    </div>
    <div class="footer">
      <FooterComp />
    </div>
  </div>
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

.main-app {
  position: relative;
}
.app {
  display: flex;
  main {
    flex: 1 1 0;
    padding-left: 6rem;
    min-height: 100vh;
    padding-bottom: 6rem;

    @media (max-width: 768px) {
      padding-left: 6rem;
    }
  }
}

.footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  z-index: 100 !important;
}
</style>
