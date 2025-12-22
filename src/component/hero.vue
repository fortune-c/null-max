<script setup>
import { ref } from 'vue'

const showVideo = ref(false)

const openVideo = () => {
  showVideo.value = true
}

const closeVideo = () => {
  showVideo.value = false
}
</script>

<template>
  <div class="flex flex-col justify-center items-center h-screen">
    <h1
      class="bg-linear-to-b from-indigo-700 via-purple-400 to-pink-700 bg-clip-text text-8xl max-sm:text-6xl z-0"
    >
      NULLMAX
    </h1>
    <img
      src="../assets/hero-headphones.png"
      alt="Hero Headphones"
      class="absolute mt-10 rounded-lg shadow-lg z-30"
    />
    <!-- <video autoplay muted loop class="w-3/4 mt-10 rounded-lg shadow-lg z-10 absolute">
            <source src="../assets/hero-headphones.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video> -->
  </div>
  <div
    class="mx-10 flex flex-row space-x-55 max-sm:flex-col max-sm:space-x-0 max-sm:space-y-4 max-sm:mx-4 mb-10"
  >
    <div class="flex flex-col text-left">
      <p class="text-gray-600">
        Experience unparalleled sound quality <br />
        with NullMax headphones,<br />
        designed for comfort and <br />
        engineered for excellence.<br />
        Dive into a world of immersive audio and stylish design.<br />
      </p>
      <button
        @click="openVideo"
        class="bg-[#1a1a1a] w-30 h-5 rounded-[20px] flex items-center justify-center text-[13px] font-bold text-white py-4 my-2"
      >
        Watch Demo
      </button>
      <!-- Video Modal -->
      <div v-if="showVideo" class="fixed inset-0 z-50 flex items-center justify-center bg-black/80">
        <!-- Close button -->
        <button @click="closeVideo" class="absolute top-15 right-60 z-60 text-white text-2xl font-bold">
          &times;
        </button>

        <!-- Video -->
        <video controls autoplay class="w-11/12 max-w-4xl rounded-xl shadow-2xl">
          <source src="../assets/hero-headphones.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
      </div>
    </div>
    <p class="text-gray-600">
      Precision.
      <span class="bg-clip-text text-transparent bg-linear-to-l from-[#9AE6B4] to-[#FEF3C7]">
        Power.
      </span>
      Purity.
    </p>
    <p class="text-gray-600 font-extralight text-right">
      Ships Starting <span class="text-white font-extrabold">July 15 · </span>Limited <br />
      Quantities Available
    </p>
  </div>
</template>
