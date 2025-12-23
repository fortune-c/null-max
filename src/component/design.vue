<script setup>
import { ref, onMounted } from 'vue'

const showHeadings = ref(false)

onMounted(() => {
  const headings = document.querySelector('#color')

  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        showHeadings.value = true
        observer.unobserve(headings) // stop observing after it's visible
      }
    },
    { threshold: 0.2 },
  )

  observer.observe(headings)
})

const colors = [
  {
    name: 'Graphite Black',
    img: new URL('../assets/black-headphones.png', import.meta.url).href,
    circle: 'bg-black',
  },
  {
    name: 'Silver White',
    img: new URL('../assets/white-headphones.png', import.meta.url).href,
    circle: 'bg-gray-300',
  },
  {
    name: 'Forest Green',
    img: new URL('../assets/green-headphones.png', import.meta.url).href,
    circle: 'bg-green-600',
  },
  {
    name: 'Ocean Blue',
    img: new URL('../assets/blue-headphones.png', import.meta.url).href,
    circle: 'bg-blue-600',
  },
]

const selectedColor = ref(colors[0])
</script>

<template>
  <div class="mx-10 flex flex-col items-center space-y-8" id="color">
    <!-- Title -->
    <Transition name="slide-left">
      <div v-if="showHeadings" class="pt-10 text-center">
        <h4 class="text-[#6EE7BA]">DESIGN & BUILD</h4>
        <p class="text-4xl text-white font-extrabold max-sm:text-3xl mt-3">Choose your Style.</p>
      </div>
    </Transition>

    <!-- Headphone Image -->
    <img
      :src="selectedColor.img"
      alt="Headphones"
      class="w-90 h-auto rounded-lg shadow-lg transition-all duration-500"
    />

    <!-- Color Name -->
    <h3 class="text-white my-2 text-lg">
      {{ selectedColor.name }}
    </h3>

    <!-- Color Selector -->
    <div class="flex items-center space-x-4">
      <button
        v-for="color in colors"
        :key="color.name"
        @click="selectedColor = color"
        class="w-8 h-8 rounded-full border-2 transition-all duration-300"
        :class="[
          color.circle,
          selectedColor.name === color.name ? 'border-white scale-110' : 'border-white/30',
        ]"
      ></button>
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
