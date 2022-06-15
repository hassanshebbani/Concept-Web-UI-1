<template>
  <header ref="navbar" class="hidden lg:flex items-center justify-between">
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
  <!-- Clip nav -->
  <div
    class="burger2 inline-block lg:hidden absolute top-10 right-10"
    ref="burger"
  >
    <div class="line1"></div>
    <div class="line2"></div>
  </div>
  <nav class="nav-bar lg:hidden px-10 lg:px-0">
    <ul class="nav-links">
      <h3 v-for="(link, index) in navLinks" :key="index">{{ link }}</h3>
    </ul>
    <div class="contact">
      <h2>Stay in touch!</h2>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nam in,
        deleniti, vero minus molestiae saepe earum amet voluptate ipsa, debitis
        consectetur dicta neque necessitatibus incidunt facere. Nulla optio
        praesentium adipisci.
      </p>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import gsap from "gsap";
const navLinks: String[] = ["About", "Service", "Portfolio", "Blog", "Contact"];
const navbar = ref<HTMLElement>();
const burger = ref();

const animateNav = () => {
  gsap.fromTo(
    navbar.value!,
    1,
    { y: "-100%" },
    { y: "0%", delay: 0.5, ease: "power2.out" }
  );
};

const close_overlay_nav = () => {
  gsap.to(".line1", 0.5, { rotate: "0", y: 0, background: "white" });
  gsap.to(".line2", 0.5, { rotate: "0", y: 0, background: "white" });
  gsap.to("#logo", 1, { color: "white" });
  gsap.to(".nav-bar", 0.75, { clipPath: "circle(50px at 100% -10%)" });
};

const navToggle = (e: Event) => {
  // <HTMLDivElement>e.target is the same as e.target as HTMLDivElement
  if (!(<HTMLDivElement>e.target)!.classList.contains("active")) {
    (<HTMLDivElement>e.target)!.classList.add("active");
    gsap.to(".line1", 0.5, { rotate: "45", y: 3, background: "black" });
    gsap.to(".line2", 0.5, { rotate: "-45", y: -3, background: "black" });
    gsap.to("#logo", 1, { color: "black" });
    gsap.to(".nav-bar", 1, { clipPath: "circle(2500px at 100% -10%)" });
    document.body.classList.add("hide");
  } else {
    (<HTMLDivElement>e.target)!.classList.remove("active");
    close_overlay_nav();
    document.body.classList.remove("hide");
  }
};

onMounted(async () => {
  animateNav();
  burger.value!.addEventListener("click", navToggle);
  window.addEventListener("resize", () => {
    const vw: Number = window.innerWidth;
    if (vw > 1024 && !navbar.value!.classList.contains("hide"))
      return close_overlay_nav();
  });
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
    button {
      border-radius: 2.5rem;
      background: #8976f7;
      font-size: 1.75rem;
      padding: 1rem 2rem;
    }
  }
}

.burger2 {
  cursor: pointer;
  z-index: 10;
  .line1,
  .line2 {
    width: 3rem;
    height: 0.2rem;
    margin: 0.4rem;
    background: white;
    pointer-events: none;
  }
}

.nav-bar {
  @include flex(row, center, space-around);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: white;
  z-index: 1;
  opacity: 1;
  clip-path: circle(50px at 100% -10%);
  .nav-links {
    font-size: 3rem;
    flex-basis: 30rem;
    h3 {
      padding: 3rem 0rem;
    }
  }
  .contact {
    flex-basis: 30rem;
    h2 {
      font-size: 3rem;
      padding: 2rem 0rem;
    }
    p {
      font-size: 1.5rem;
      line-height: 2rem;
    }
  }
}
</style>
