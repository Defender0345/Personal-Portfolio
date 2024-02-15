<template>
  <aside :class="`${is_expanded ? 'is-expanded' : ''}`">
    <div class="my-logo">
      <a href="index.html" class="home-link"
        ><img src="@/assets/Images/logo.png" alt="My Portfolio" class="sidebar-img"
      /></a>
    </div>

    <div class="menu-toggle-wrap">
      <button class="menu-toggle" @click="ToggleMenu">
        <i class="fa-solid fa-arrow-right sidebar-icon"></i>
      </button>
    </div>

    <h3>Menu</h3>
    <div class="menu">
      <router-link to="/" class="button">
        <i class="fa-solid fa-house sidebar-icon"></i>
        <span class="text">Home</span>
      </router-link>
      <router-link to="/work" class="button">
        <i class="fa-brands fa-github sidebar-icon"></i>
        <span class="text">Work</span>
      </router-link>
      <router-link to="/about" class="button">
        <i class="fa-solid fa-user sidebar-icon"></i>
        <span class="text">About</span>
      </router-link>
      <router-link to="/game" class="button">
        <i class="fa-solid fa-gamepad sidebar-icon"></i>
        <span class="text">Game</span>
      </router-link>
      <router-link to="/contact" class="button">
        <i class="fa-solid fa-envelope sidebar-icon"></i>
        <span class="text">Contact</span>
      </router-link>
    </div>
    <div class="flex"></div>
  </aside>
</template>

<script setup>
import { ref } from 'vue'

const is_expanded = ref(localStorage.getItem('is_expanded') === 'true')

const ToggleMenu = () => {
  is_expanded.value = !is_expanded.value
  localStorage.setItem('is_expanded', is_expanded.value)
}
</script>

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

.app {
  display: flex;
  main {
    flex: 1 1 0;
    padding: 2rem;

    @media (max-width: 768px) {
      padding-left: 6rem;
    }
  }
}

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

  background-color: var(--dark);
  color: var(--light);

  width: calc(2rem + 32px);
  overflow: hidden;
  min-height: 100vh;
  padding: 1rem;
  position: absolute;
  z-index: 99;

  transition: 0.2s ease-out;

  .flex {
    margin-bottom: 1rem;
  }

  .my-logo {
    align-items: center;
    margin-bottom: 1rem;

    .home-link {
      width: 2rem;
      .sidebar-img {
        width: 2rem;
      }
    }
  }

  .menu-toggle-wrap {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 1rem;
    position: relative;
    top: 0;
    transition: 0.2s ease-in-out;

    .menu-toggle {
      transition: 0.2s ease-in-out;
      .sidebar-icon {
        width: 2rem;
        color: var(--light);
        transition: 0.2s ease-out;
      }

      &:hover {
        .sidebar-icon {
          color: var(--primary);
          transform: translateX(0.5rem);
        }
      }
    }
  }

  h3,
  .button .text {
    opacity: 0;
    transition: opacity 0.3s ease-in-out;
  }

  h3 {
    color: var(--grey);
    font-size: 0.875rem;
    margin-bottom: 0.5rem;
    text-transform: uppercase;
  }

  .menu {
    height: 50vh;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    // margin: 0 -1rem;

    .button {
      display: flex;
      align-items: center;
      text-decoration: none;
      transition: 0.2s ease-in-out;
      padding: 0.5rem 1rem;

      .sidebar-icon {
        font-size: 2rem;
        color: var(--light);
        transition: 0.2s ease-in-out;
      }

      .text {
        color: var(--light);
        transition: 0.2s ease-in-out;
      }

      &:hover {
        background-color: var(--dark-alt);

        .sidebar-icon,
        .text {
          color: var(--primary);
        }
      }

      &.router-link-exact-active {
        background-color: var(--dark-alt);
        border-right: 5px solid var(--primary);

        .sidebar-icon,
        .text {
          color: var(--primary);
        }
      }
    }
  }

  &.is-expanded {
    width: var(--sidebar-width);

    .menu-toggle-wrap {
      top: -3rem;

      .menu-toggle {
        transform: rotate(-180deg);
      }
    }

    h3,
    .button .text {
      opacity: 1;
    }

    .button {
      .sidebar-icon {
        margin-right: 1rem;
      }
    }
  }

  @media (max-width: 768px) {
    position: fixed;
    z-index: 99;
  }
}
</style>
