<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const hidden = ref(false)
const scrolled = ref(false)

let lastScrollY = window.scrollY

const onScroll = () => {
  const current = window.scrollY

  hidden.value = current > lastScrollY && current > 80
  scrolled.value = current > 10

  lastScrollY = current
}

onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<template>
  <nav
    class="sticky top-0 z-50 flex items-center justify-between p-4 text-white mx-10 bg-black/80 backdrop-blur transition-all duration-300"
    :class="{
      'border-b border-white/30': scrolled,
    }"
  >
    <a href="#">NullMax</a>
    <ul class="flex flex-row space-x-4 max-sm:hidden">
      <li><a href="#features" class="hover:text-gray-700">Features</a></li>
      <li><a href="#color" class="hover:text-gray-700">Color</a></li>
      <li><a href="#pricing" class="hover:text-gray-700">Pricing</a></li>
      <li><a href="#contact" class="hover:text-gray-700">Contact</a></li>
    </ul>
    <a
      href="#"
      class="rounded-md bg-gray-600 px-2 text-xs w-20 h-6 text-center flex items-center justify-center hover:text-gray-400"
      >Preorder</a
    >
  </nav>
</template>
