<script setup>
import { ref, onMounted } from 'vue'

const showVideo = ref(false)
const showTitle = ref(false)
const showParagraph = ref(false)

const openVideo = () => {
  showVideo.value = true
}

const closeVideo = () => {
  showVideo.value = false
}

onMounted(() => {
  setTimeout(() => {
    showTitle.value = true
  }, 500)
})

onMounted(() => {
  const paragraph = document.querySelector('#meet-nullmax')

  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        showParagraph.value = true
        observer.unobserve(paragraph) // stop observing after it's visible
      }
    },
    { threshold: 0.2 },
  )

  observer.observe(paragraph)
})
</script>

<template>
  <div class="flex flex-col justify-center items-center h-screen">
    <Transition name="slide-down">
      <h1
        class="bg-linear-to-b from-indigo-700 via-purple-400 to-pink-700 bg-clip-text text-8xl max-sm:text-6xl z-0"
        v-if="showTitle"
      >
        NULLMAX
      </h1>
    </Transition>

    <img
      src="../assets/hero-headphones.png"
      alt="Hero Headphones"
      class="absolute mt-10 rounded-lg shadow-lg z-30"
    />
  </div>
  <div
    class="mx-10 flex flex-row justify-center space-x-64 max-sm:flex-col max-sm:space-x-0 max-sm:space-y-4 max-sm:mx-4 mb-10"
  >
    <div class="flex flex-col text-left">
      <p class="text-gray-600">
        Industry-leading noise<br />
        cancellation and stunning<br />
        minimalist design.
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
        <button
          @click="closeVideo"
          class="absolute top-15 right-60 z-60 text-white text-2xl font-bold"
        >
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
  <div class="mx-10 flex items-center space-x-10 max-sm:flex-col ">
    <img
      src="../assets/model-with-headphone.png"
      alt="Waveform"
      class="w-90 h-auto rounded-lg shadow-lg z-0"
    />
    <div class="pt-10 bg-black-800" id="meet-nullmax">
      <h4 class="text-[#6EE7BA]">MEET NULLMAX</h4>
      <Transition name="slide-left">
        <p
          v-if="showParagraph"
          class="text-4xl text-white font-extrabold max-sm:text-3xl mt-3"
        >
          Experience unparalleled sound quality <br />
          with NullMax headphones, designed <br />
          for comfort and engineered for excellence.<br />
          Dive into a world of immersive audio and stylish design.<br />
        </p>
      </Transition>
    </div>
  </div>
  
</template>

<style scoped>
.slide-down-enter-active {
  transition: all 0.8s ease-out;
}

.slide-down-enter-from {
  opacity: 0;
  transform: translateY(-60px);
}

.slide-down-enter-to {
  opacity: 1;
  transform: translateY(0);
}

.slide-left-enter-active {
  transition: all 0.8s ease-out;
}

.slide-left-enter-from {
  opacity: 0;
  transform: translateX(-100px);
}

.slide-left-enter-to {
  opacity: 1;
  transform: translateX(0);
}

</style>
