<script setup>
import { defineAsyncComponent, ref } from "vue";
const Modal = defineAsyncComponent(() => import("../components/Modal.vue"));
const modalActive = ref(null);
const toggleModal = () => {
  modalActive.value = !modalActive.value;
};

const animateString = (word) => {
  let str = word;
  let split = str.split("");
  let html = "";
  for (let i = 0; i < split.length; i++) {
    const style = `animation-delay:${0.5 + i / 10 + "s"}`;
    html += `<span class="text-green" style=${style}>` + split[i] + "</span>";
  }
  return html;
};

const heading = animateString("Explore");
// console.log(heading);
</script>

<template>
  <div class="flex flex-col justify-end w-screen h-screen bg-cover hero">
    <div class="xl:pl-60 xl:pt-16">
      <!-- <h1 class="text-white font-serif" id="explore" v-html="heading"></h1> -->
      <h1
        class="text-white font-serif transition-opacity"
        id="explore"
        :class="[{ 'opacity-0': modalActive }]"
      >
        <span class="fade-in" style="animation-delay: 0.1s">E</span
        ><span class="fade-in" style="animation-delay: 0.3s">x</span
        ><span class="fade-in" style="animation-delay: 0.5s">p</span
        ><span class="fade-in" style="animation-delay: 0.7s">l</span
        ><span class="fade-in" style="animation-delay: 0.9s">o</span
        ><span class="fade-in" style="animation-delay: 1.1s">r</span
        ><span class="fade-in" style="animation-delay: 1.3s">e</span>
      </h1>
      <button
        id="myBtn"
        class="mt-4 flex items-center text-white text-xl font-light ml-8"
        :class="{ 'opacity-0': modalActive }"
        @click="toggleModal"
      >
        <span class="mr-2 info-fade-in"><img src="../assets/Plus.svg" /></span>
        <span class="mr-2 text-2xl font-bold info-fade-in">More Details</span>
        <Modal :modalActive="modalActive" @close-modal="toggleModal"> </Modal>
      </button>
    </div>
    <div class="flex justify-end p-8">
      <div class="flex xl:flex-col">
        <a
          href="https://facebook.com"
          target="_blank"
          class="text-white text-4xl mr-2 xl:mb-4 shadow-md"
          ><img src="../assets/Facebook.svg" alt="Facebook icon"
        /></a>
        <a href="https://instagram.com" target="_blank" class="mb-4 shadow-md"
          ><img src="../assets/Instagram.svg" alt="Instagram icon"
        /></a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.hero {
  background: linear-gradient(
      90deg,
      rgba(97, 24, 24, 1) 30%,
      rgba(0, 0, 0, 0) 30%
    ),
    url("../assets/small_res.png");
  background-position: top right;
  background-repeat: no-repeat;
  background-size: fixed;
}

.icon {
  display: inline-block;
  width: 1rem;
  height: 1rem;
  background-size: cover;
}
.icon-facebook {
  background-image: url(../assets/Facebook.svg);
}

#explore {
  font-size: 10rem;
  line-height: 0.95;
}

@media (width <= 1250px) {
  #explore {
    font-size: 5rem;
    line-height: 0.95;
    margin-left: 2rem;
  }

  .hero {
    background: url("../assets/small_res.png");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
}

@media (width <= 1250px) {
  .icon-container {
    stroke: green;
  }
}

.fade-in {
  position: relative;
  opacity: 0;
  animation: fadeInAnimation ease-in 0.6s forwards;
}
.info-fade-in {
  position: relative;
  opacity: 0;
  animation: fadeInAnimation ease 300ms forwards;
  animation-delay: 2.2s;
}

@keyframes fadeInAnimation {
  0% {
    bottom: -0.1em;
    opacity: 0;
  }

  100% {
    bottom: 0;
    opacity: 1;
  }
}
</style>
