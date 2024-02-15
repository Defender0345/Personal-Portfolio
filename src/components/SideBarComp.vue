<template>
  <aside>
    <div class="logo">
      <a href="index.html" class="home-link"
        ><img src="@/assets/Images/logo.png" alt="My Portfolio" class="sidebar-img"
      /></a>
    </div>

    <div class="menu-toggle-wrap">
      <button class="menu-toggle">
        <i class="fa-solid fa-arrow-right"></i>
      </button>
    </div>
  </aside>
</template>

<script setup></script>

<style lang="scss">
:root {
  --primary: #4ade80;
  --primary-alt: #22c55e;
  --grey: #64748b;
  --dark: #1e293b;
  --dark-alt: #334155;
  --light: #f1f5f9;
  --sidebar-width: 300px;
}

// .app {
//   display: flex;
//   main {
//     flex: 1 1 0;
//     padding: 2rem;

//     @media (max-width: 768px) {
//       padding-left: 6rem;
//     }
//   }
// }

button {
  cursor: pointer;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}

aside {
  display: flex;
  flex-direction: column;
  width: calc(2rem + 2rem);
  overflow: hidden;
  min-height: 100vh;
  padding: 1rem;
  position: absolute;
  z-index: 99;

  background-color: var(--dark);
  color: var(--light);

  transition: 0.2s ease-out;

  .my-logo {
    margin-bottom: 1rem;
    .home-link {
      width: 2rem;
      .sidebar-img {
        width: 2rem;
      }
    }
  }

  .menu-toggle-wrap {
    .menu-toggle {
      .fa-arrow-right {
        width: 2rem;
      }
    }
  }

  @media (max-width: 768px) {
    position: fixed;
    z-index: 99;
  }
}
</style>
