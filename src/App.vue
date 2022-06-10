<template>
  <div class="bg-stuff" ref="bg">
    <svg
      class="svg-top-left"
      viewBox="0 0 469 312"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M0.5 0.5V311.5C105.5 257 82 144 163.5 144C252.051 144 264.5 167 343 144C402 126.713 450.333 40.6667 468.5 0.5H0.5Z"
        fill="url(#paint0_linear_1_3)"
      />
      <defs>
        <linearGradient
          id="paint0_linear_1_3"
          x1="-7.6047e-08"
          y1="8.49528e-08"
          x2="234.5"
          y2="311.5"
          gradientUnits="userSpaceOnUse"
        >
          <stop stop-color="#4A2BFC" />
          <stop offset="1" stop-color="#8976F7" stop-opacity="0.74" />
        </linearGradient>
      </defs>
    </svg>
    <svg
      class="svg-bottom-right"
      viewBox="0 0 469 336"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M468.002 336L468 25C473.5 -19 431.502 -2.15097 377.002 60.5C327.727 117.145 338.002 197.5 276.002 222.5C193.877 255.615 185.003 199.5 106.503 222.5C47.5028 239.787 18.1695 295.833 0.00283813 336L468.002 336Z"
        fill="url(#paint0_linear_1_4)"
      />
      <defs>
        <linearGradient
          id="paint0_linear_1_4"
          x1="468.5"
          y1="336.5"
          x2="234"
          y2="24.9997"
          gradientUnits="userSpaceOnUse"
        >
          <stop stop-color="#4A2BFC" />
          <stop offset="1" stop-color="#8976F7" stop-opacity="0.74" />
        </linearGradient>
      </defs>
    </svg>
    <div class="outline-circle"></div>
    <div class="head-orange-circle"></div>
    <div class="right-circle"></div>
    <div class="left-half-circle"></div>
    <div class="top-small-circle"></div>
    <div class="middle-small-circle"></div>
  </div>
  <NavVue />
  <MainVue />
  <FooterVue />
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";
import gsap from "gsap";
import NavVue from "./components/Nav.vue";
import MainVue from "./components/Main.vue";
import FooterVue from "./components/Footer.vue";

const bg = ref<HTMLDivElement>();

const animateBg = () => {
  gsap.fromTo(
    bg.value!,
    0.75,
    { zIndex: -10, opacity: 0, scale: 1.2 },
    { zIndex: -10, opacity: 1, scale: 1, delay: 6, ease: "power2.inOut" }
  );
};

onMounted(async () => {
  animateBg();
});
</script>

<style lang="scss" scoped>
/*
 nav 8vh
 main 70vh
 footer 22vh
*/

.bg-stuff {
  position: relative;
  .outline-circle,
  .head-orange-circle,
  .right-circle,
  .left-half-circle,
  .top-small-circle,
  .middle-small-circle {
    position: absolute;
    background: #fff;
    opacity: 0.05;
    border-radius: 50%;
  }
  .outline-circle {
    top: 10rem;
    left: 37%;
    width: 28rem;
    height: 28rem;
    background: transparent;
    border: 4rem white solid;
  }
  .head-orange-circle {
    top: 5rem;
    right: 15%;
    width: 42rem;
    height: 42rem;
    background: linear-gradient(to top, #ec787b, #fc4b51);
    opacity: 1;
    z-index: -1;
  }
  .right-circle {
    top: 20rem;
    right: 4%;
    width: 8rem;
    height: 8rem;
  }
  .left-half-circle {
    top: 45rem;
    left: -2%;
    width: 8rem;
    height: 8rem;
  }
  .top-small-circle {
    top: 3rem;
    left: 57%;
    width: 4rem;
    height: 4rem;
  }
  .middle-small-circle {
    top: 60rem;
    left: 40%;
    width: 4rem;
    height: 4rem;
  }
  .svg-top-left,
  .svg-bottom-right {
    position: absolute;
    width: 45rem;
    height: 45rem;
    z-index: -1;
  }
  .svg-top-left {
    width: 40rem;
    height: 40rem;
    top: -10rem;
    left: 0%;
  }
  .svg-bottom-right {
    top: 40rem;
    // bottom: 50%;
    right: -4%;
  }
}
</style>
