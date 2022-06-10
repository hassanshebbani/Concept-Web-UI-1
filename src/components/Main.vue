<template>
  <main class="">
    <!-- Left Side -->
    <div class="left w-full xl:w-7/12">
      <h3 class="-mb-0 xl:-mb-12" ref="myName">I'm Hassan Shebbani</h3>
      <h1 ref="title">Creating Easier Solutions</h1>
      <p class="w-full xl:w-3/4" ref="subtitle">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt id
        voluptates laudantium quos? Rem magni dolores commodi atque aut.
      </p>
      <!-- CTA Buttons -->
      <div class="buttons">
        <button ref="ctaOrange">LET'S WORK</button>
        <div class="portfolio-btn" ref="ctaPortfolio">
          <div class="play">
            <svg
              version="1.0"
              xmlns="http://www.w3.org/2000/svg"
              width="799.000000pt"
              height="1280.000000pt"
              viewBox="0 0 799.000000 1280.000000"
              preserveAspectRatio="xMidYMid meet"
            >
              <metadata>
                Created by potrace 1.15, written by Peter Selinger 2001-2017
              </metadata>
              <g
                transform="translate(0.000000,1280.000000) scale(0.100000,-0.100000)"
                fill="#ec787b"
                stroke="none"
              >
                <path
                  d="M6905 12069 c-495 -402 -1168 -948 -1495 -1214 -327 -265 -1677
-1361 -3000 -2434 l-2405 -1952 0 -69 0 -69 2405 -1952 c1323 -1073 2673
-2169 3000 -2434 327 -266 1000 -812 1495 -1214 l900 -731 93 0 92 0 0 6400 0
6400 -92 0 -93 0 -900 -731z"
                />
              </g>
            </svg>
          </div>
          <span>PORTFOLIO</span>
        </div>
      </div>
      <!-- Testimonial -->
      <div class="testimonial-container">
        <img ref="testImg" src="/assets/images/girl.jpg" alt="Some girl" />
        <div ref="testText" class="testimonial">
          <p>We had reached a great height in atmosphere</p>
          <span>Celty Sturluson</span>
        </div>
      </div>
    </div>
    <!--  -->
    <!-- Right Side -->
    <div class="right hidden lg:flex">
      <img ref="rightImg" src="/assets/images/rdj.png" alt="Robert Downey Jr." />
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import gsap from "gsap";

const myName = ref<HTMLHeadingElement>();
const title = ref<HTMLHeadingElement>();
const subtitle = ref<HTMLParagraphElement>();
const ctaOrange = ref<HTMLButtonElement>();
const ctaPortfolio = ref<HTMLButtonElement>();
const testImg = ref<HTMLImageElement>();
const testText = ref<HTMLDivElement>();
const rightImg = ref<HTMLImageElement>();

const animateMain = () => {
  const mainTl: GSAPTimeline = gsap.timeline({
    defaults: {
      duration: 0.75,
      ease: "power2.inOut",
    },
  });
  mainTl.fromTo(myName.value!, {opacity: 0, y: "50%"}, {opacity: 1, y: "0%"}, "+=1")
  mainTl.fromTo(title.value!, {opacity: 0, y: "20%"}, {opacity: 1, y: "0%"}, "-=0.35")
  mainTl.fromTo(subtitle.value!, {opacity: 0, y: "20%"}, {opacity: 1, y: "0%"}, "-=0.35")
  mainTl.fromTo(ctaOrange.value!, {opacity: 0, y: "20%"}, {opacity: 1, y: "0%"}, "-=0.35")
  mainTl.fromTo(ctaPortfolio.value!, {opacity: 0, x: "30%"}, {opacity: 1, x: "0%"}, "-=0.35")
  mainTl.fromTo(testImg.value!, {opacity: 0, scale: 0}, {opacity: 1, scale: 1}, "-=0.35")
  mainTl.fromTo(testText.value!, {opacity: 0, x: "10%"}, {opacity: 1, x: "0%"}, "-=0.35")
  mainTl.fromTo(rightImg.value!, {opacity: 0, y: "20%"}, {opacity: 1, y: "0%"}, "+=1.35")
};

onMounted(async () => {
  animateMain();
});
</script>

<style lang="scss" scoped>
@mixin flex($direction, $align, $justify) {
  display: flex;
  flex-direction: $direction;
  align-items: $align;
  justify-content: $justify;
}
main {
  @include flex(row, center, space-between);
  width: 85%;
  min-height: 68vh;
  margin: auto;
  .left {
    @include flex(column, flex-start, space-around);
    // width: 60%;
    min-height: 68vh;
    // height: 100%;
    padding: 2rem 0rem;
    color: white;
    h3 {
      color: #ec787b;
      font-size: 2rem;
    }
    h1 {
      font-size: clamp(3rem, 10vw, 10rem);
      line-height: clamp(5rem, 10vw, 9rem);
      font-weight: 700;
    }
    p {
      font-size: clamp(1.25rem, 4vw, 1.75rem);
      opacity: 0.7;
    }
    .buttons {
      @include flex(row, center, space-between);
      button {
        padding: 1rem 2rem;
        background: #ec787b;
        border-radius: 2.5rem;
        font-size: 1.5rem;
        font-weight: bold;
      }
      .portfolio-btn {
        @include flex(row, center, center);
        cursor: pointer;
        margin-left: 3rem;
        .play {
          @include flex(row, center, center);
          border: 0.15rem white solid;
          border-radius: 100%;
          width: 4rem;
          height: 4rem;
          padding: 1rem;
          opacity: 0.7;
          svg {
            width: 1.5rem;
            height: 1.5rem;
            transform: rotateY(180deg) translate(-5%, 5%);
          }
        }
        span {
          font-size: 1.5rem;
          margin-left: 1.5rem;
        }
      }
    }
    .testimonial-container {
      @include flex(row, flex-start, center);
      img {
        border: 0.2rem black solid;
        outline: 0.3rem #ec787b solid;
        border-radius: 50%;
        width: 8rem;
        height: 8rem;
        object-fit: cover;
        margin-right: 2rem;
      }
      .testimonial {
        @include flex(column, flex-start, space-between);
        p {
          width: 60%;
          font-size: 2rem;
          line-height: 3rem;
          font-weight: 400;
          opacity: 1;
          margin-bottom: 3rem;
        }
        span {
          font-size: 1.5rem;
          opacity: 0.5;
        }
      }
    }
  }
  .right {
    // height: ;
    height: 70vh;
    width: 40%;

    img {
      width: 100%;
      height: 100%;
      // transform: scale(1.25);
      margin-right: 10rem;
      object-fit: cover;
    }
  }
}
</style>
