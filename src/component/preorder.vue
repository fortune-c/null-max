<script setup>
import { ref, onMounted } from 'vue'

const showComponent = ref(false)

onMounted(() => {
  const component = document.querySelector('#preorder')

  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        showComponent.value = true
        observer.unobserve(component) // stop observing after it's visible
      }
    },
    { threshold: 0.2 },
  )

  observer.observe(component)
})
</script>

<template>
  <div class="mx-10 flex flex-col items-center space-y-2 my-40" id="preorder">
    <!-- Title -->
    <Transition name="slide-left">
      <div v-if="showComponent" class="pt-10 text-center">
        <h4 class="text-[#6EE7BA]">PRICING</h4>
        <p class="text-4xl text-white font-extrabold max-sm:text-3xl mt-3">Pre‑order opens soon.</p>
        <P class="text-[12px] text-gray-500 font-light mb-2"
          >Be the first to know when pricing goes live. Use the contact form below to get
          notified.</P
        >
        <a
          href="#contact"
          class="bg-white text-black w-20 h-7 py-1 px-3 rounded-[10px] hover:bg-gray-200"
          >Contact Sales</a
        >
      </div>
    </Transition>
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
