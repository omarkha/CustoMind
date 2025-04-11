<template>
  <nav class="navbar">
    <div class="brand">
      <h1>CustoMind</h1>
      <span class="tagline">Customer Intelligence Platform</span>
    </div>

    <!-- Desktop Navigation -->
    <ul class="nav-links">
      <li class="nav-item">
        <a href="#services">
          <font-awesome-icon :icon="['fas', 'chart-line']" class="nav-icon" />
          <span class="nav-text">Solutions</span>
        </a>
      </li>
      <li class="nav-item">
        <a href="#about">
          <font-awesome-icon :icon="['far', 'lightbulb']" class="nav-icon" />
          <span class="nav-text">Our Approach</span>
        </a>
      </li>
      <li class="nav-item">
        <a href="#contact">
          <font-awesome-icon :icon="['fas', 'headphones']" class="nav-icon" />
          <span class="nav-text">Get Started</span>
        </a>
      </li>
    </ul>

    <!-- Mobile Menu Button -->
    <button class="mobile-menu-button" @click="toggleMenu">
      <font-awesome-icon
        :icon="isMenuOpen ? ['fas', 'xmark'] : ['fas', 'bars']"
      />
    </button>

    <!-- Mobile Navigation -->
    <transition name="slide-down">
      <ul v-if="isMenuOpen" class="mobile-nav-links">
        <li class="nav-item">
          <a href="#services" @click="closeMenu">
            <font-awesome-icon :icon="['fas', 'chart-line']" class="nav-icon" />
            <span>Customer Intelligence Solutions</span>
          </a>
        </li>
        <li class="nav-item">
          <a href="#about" @click="closeMenu">
            <font-awesome-icon :icon="['far', 'lightbulb']" class="nav-icon" />
            <span>Our Methodology</span>
          </a>
        </li>
        <li class="nav-item">
          <a href="#contact" @click="closeMenu">
            <font-awesome-icon :icon="['fas', 'headphones']" class="nav-icon" />
            <span>Schedule Demo</span>
          </a>
        </li>
      </ul>
    </transition>
  </nav>
</template>

<script setup>
import { ref } from "vue";
import { library } from "@fortawesome/fontawesome-svg-core";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

// Import solid icons
import {
  faChartLine,
  faHeadphones,
  faXmark,
  faBars,
} from "@fortawesome/free-solid-svg-icons";

// Import regular icons
import { faLightbulb } from "@fortawesome/free-regular-svg-icons";

// Add icons to library
library.add(faChartLine, faHeadphones, faXmark, faBars, faLightbulb);

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = () => {
  isMenuOpen.value = false;
};
</script>

<style lang="scss" scoped>
.navbar {
  position: sticky;
  top: 0;
  height: 80px;
  width: 100%;
  background-color: hsla(233, 62%, 23.6%, 95%);
  padding: 0 10%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.2);
  color: #fff;
  z-index: 1000;
  backdrop-filter: blur(8px);

  .brand {
    display: flex;
    flex-direction: column;

    h1 {
      font-family: "PT Sans", sans-serif;
      color: hsl(55, 100%, 50%);
      font-size: 1.8rem;
      text-shadow: 1px 2px 1px hsl(232, 100%, 62%);
      margin: 0;
      line-height: 1;
    }

    .tagline {
      font-size: 0.7rem;
      color: hsl(232, 100%, 85%);
      letter-spacing: 1px;
      margin-top: 4px;
    }
  }

  .nav-links {
    list-style: none;
    display: flex;
    gap: 2rem;
    margin: 0;
    padding: 0;

    @media (max-width: 768px) {
      display: none;
    }

    .nav-item {
      position: relative;

      a {
        display: flex;
        align-items: center;
        gap: 8px;
        color: hsl(232, 100%, 85%);
        text-decoration: none;
        font-weight: 500;
        font-size: 0.95rem;
        padding: 0.5rem 0;
        transition: all 0.3s ease;

        .nav-icon {
          font-size: 0.9rem;
          transition: all 0.3s ease;
        }

        &:hover {
          color: hsl(232, 100%, 95%);

          .nav-icon {
            transform: translateY(-2px);
            color: hsl(55, 100%, 50%);
          }
        }
      }

      &::after {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        width: 0;
        height: 2px;
        background: hsl(55, 100%, 50%);
        transition: width 0.3s ease;
      }

      &:hover::after {
        width: 100%;
      }
    }
  }

  .mobile-menu-button {
    display: none;
    background: none;
    border: none;
    color: hsl(232, 100%, 85%);
    font-size: 1.5rem;
    cursor: pointer;
    transition: all 0.3s ease;

    &:hover {
      color: hsl(55, 100%, 50%);
      transform: scale(1.1);
    }

    @media (max-width: 768px) {
      display: block;
    }
  }

  .mobile-nav-links {
    position: absolute;
    top: 80px;
    left: 0;
    width: 100%;
    background: hsla(233, 62%, 15%, 98%);
    list-style: none;
    margin: 0;
    padding: 1rem 0;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);

    .nav-item {
      a {
        display: flex;
        align-items: center;
        gap: 12px;
        color: hsl(232, 100%, 85%);
        text-decoration: none;
        padding: 0.8rem 5%;
        transition: all 0.3s ease;

        .nav-icon {
          font-size: 1rem;
          color: hsl(55, 100%, 50%);
          width: 20px;
          text-align: center;
        }

        &:hover {
          background: hsla(233, 62%, 20%, 0.5);
          color: hsl(232, 100%, 95%);
          padding-left: 7%;
        }
      }
    }
  }
}

/* Animation for mobile menu */
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}

.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
