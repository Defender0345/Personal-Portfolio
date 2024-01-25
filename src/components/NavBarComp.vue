<script></script>
<template>
  <nav id="main-nav">
    <a href="index.html"><img src="@/assets/Images/logo.png" alt="My Portfolio" id="logo" /></a>
    <ul>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/work">Work</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/contact">Contact</RouterLink>
    </ul>
  </nav>
</template>

<style lang="scss">
@import '@/assets/_shared.scss';
#main-nav {
  background-color: rgba(0, 0, 0, 0.63);
}
</style>
