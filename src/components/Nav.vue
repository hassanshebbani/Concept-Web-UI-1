<template>
  <header ref="navbar">
    <!-- Left Section -->
    <div class="left-section">
      <!-- Burger Menu -->
      <div class="burger">
        <div v-for="(n, index) in 3" :key="index" :class="`line${n}`"></div>
      </div>
      <!-- Logo Text -->
      <span class="text-6xl font-bold ml-5 mr-10">PRS</span>
      <!-- Nav Links -->
      <ul class="nav-links">
        <li v-for="(link, index) in navLinks" :key="index">
          <router-link to="/">{{ link }}</router-link>
        </li>
      </ul>
    </div>
    <!-- Right Section -->
    <div class="right-section">
      <button>Contact Me</button>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import gsap from "gsap";
const navLinks: String[] = ["About", "Service", "Portfolio", "Blog", "Contact"];
const navbar = ref<HTMLElement>();

const animateNav = () => {
  gsap.fromTo(
    navbar.value!,
    1,
    { y: "-100%" },
    { y: "0%", delay: 0.5, ease: "power2.out" }
  );
};

onMounted(async () => {
  animateNav();
});
</script>

<style lang="scss" scoped>
@mixin flex($direction, $align, $justify) {
  display: flex;
  flex-direction: $direction;
  align-items: $align;
  justify-content: $justify;
}

header {
  @include flex(row, center, space-between);
  color: white;
  min-height: 8vh;
  margin: 0rem 1.5rem 0rem 1.5rem;
  .left-section {
    @include flex(row, center, center);
    .burger {
      @include flex(column, center, center);
      border: 0.2rem solid #fff;
      width: 4rem;
      height: 4rem;
      border-radius: 100%;
      padding: 0.25rem;
      opacity: 0.2;
      .line1,
      .line2,
      .line3 {
        // opacity: 0.7;
        width: 2rem;
        height: 0.2rem;
        background: #fff;
        margin: 0.25rem;
      }
    }
    // nav links
    .nav-links {
      @include flex(row, center, center);
      font-size: 1.75rem;
      li {
        opacity: 0.9;
        font-weight: 200;
        margin: 0rem 2rem;
        cursor: pointer;
      }
    }
  }
  .right-section {
    //   height: 100%;
    button {
      border-radius: 2.5rem;
      background: #8976f7;
      font-size: 1.75rem;
      padding: 1rem 2rem;
    }
  }
}
</style>
