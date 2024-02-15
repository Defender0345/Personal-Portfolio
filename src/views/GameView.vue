<script setup>
import GameComp from '@/components/GameComp.vue'
import SideBarComp from '@/components/SideBarComp.vue'
</script>

<template>
  <div class="game">
    <SideBarComp />
    <GameComp />
  </div>
</template>

<style lang="scss">
@import '@/assets/_shared.scss';
.game {
  width: 100vw;
  height: 100vh;
}
</style>
