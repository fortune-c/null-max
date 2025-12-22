<script setup>
import { ref, onMounted } from 'vue'

const showParagraph = ref(false)

onMounted(() => {
  const paragraph = document.querySelector('#features')

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
  <div class="mx-10 my-20 flex items-center justify-center max-sm:flex-col" id="features">
    <div class="pt-10 bg-black-800">
      <h4 class="text-[#6EE7BA]">Features</h4>
      <Transition name="slide-left">
        <p v-if="showParagraph" class="text-4xl text-white font-extrabold max-sm:text-3xl my-3">
          Every Note. Exactly as It<br />
          Was Meant to Be Heard<br />
          <span class="text-[12px] font-light"
            >40mm titanium drivers deliver unmatched clarity and depth — from soaring highs to
            thunderous lows. Active Noise Cancellation
          </span>
        </p>
      </Transition>
      <div class="max-w-6xl w-full grid grid-cols-1 md:grid-cols-2 gap-6">
        <!-- Card 1 -->
        <div class="relative rounded-2xl overflow-hidden group h-72 text-white">
          <img
            src="../assets/headphone1.jpg"
            class="w-full h-full object-cover group-hover:scale-105 transition duration-500"
          />
          <div class="absolute inset-0 bg-black/40"></div>
          <div class="absolute bottom-6 left-6">
            <p class="text-sm opacity-80">Active</p>
            <h3 class="text-xl font-semibold">Noise Cancellation</h3>
          </div>
        </div>

        <!-- Card 2 -->
        <div class="relative rounded-2xl overflow-hidden group h-72 text-white"">
          <img
            src="../assets/headphone2.jpg"
            class="w-full h-full object-cover group-hover:scale-105 transition duration-500"
          />
          <div class="absolute inset-0 bg-black/40"></div>
          <div class="absolute bottom-6 left-6">
            <p class="text-sm opacity-80">40-Hour Battery Life</p>
            <h3 class="text-xl font-semibold">All-Day Listening</h3>
          </div>
        </div>

        <!-- Card 3 -->
        <div class="relative rounded-2xl overflow-hidden group h-72">
          <img
            src="../assets/headphone3.jpg"
            class="w-full h-full object-cover group-hover:scale-105 transition duration-500"
          />
          <div class="absolute inset-0 bg-black/40"></div>
          <div class="absolute bottom-6 left-6">
            <p class="text-sm opacity-80">Studio-Grade</p>
            <h3 class="text-xl font-semibold">Crystal Clarity</h3>
          </div>
        </div>

        <!-- Card 4 -->
        <div class="relative rounded-2xl overflow-hidden group h-72">
          <img
            src="../assets/headphone4.jpg"
            class="w-full h-full object-cover group-hover:scale-105 transition duration-500"
          />
          <div class="absolute inset-0 bg-black/40"></div>
          <div class="absolute bottom-6 left-6">
            <p class="text-sm opacity-80 ">Hi-Res</p>
            <h3 class="text-xl font-semibold">Audio Certified</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
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
