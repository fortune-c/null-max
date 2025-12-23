<script setup>
import { ref, onMounted } from 'vue'

const showComponent = ref(false)

onMounted(() => {
  const component = document.querySelector('#contact')

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
  <div class="mx-10 flex flex-col items-center space-y-2 my-20" id="contact">
    <!-- Title -->
    <Transition name="slide-left">
      <div v-if="showComponent" class="pt-10 text-center">
        <h4 class="text-[#6EE7BA]">CONTACT</h4>
        <p class="text-4xl text-white font-extrabold max-sm:text-3xl mt-2">
          We’d love to hear from you
        </p>
        <form action="" method="post" class="text-left">
          <label for="name" class="text-white text-sm">Name</label><br />
          <input
            type="text"
            id="name"
            name="name"
            placeholder="Your Name"
            class="w-160 h-10 rounded-[10px] bg-[#0D0D0D] border border-gray-600 text-white text-sm pl-2 mb-3"
          /><br />
          <label for="email" class="text-white text-sm">Email</label><br />
          <input
            type="email"
            id="email"
            name="email"
            placeholder="you@example.com"
            class="w-160 h-10 rounded-[10px] bg-[#0D0D0D] border border-gray-600 text-white text-sm pl-2 mb-3"
          /><br />
          <label for="message" class="text-white text-sm">Message</label><br />
          <textarea
            id="message"
            name="message"
            placeholder="Tell us a bit about your request"
            rows="4"
            class="w-160 rounded-[10px] bg-[#0D0D0D] border border-gray-600 text-white text-sm pl-2 pt-2 mb-3"
          ></textarea
          ><br />
          <button
            type="submit"
            class="my-5 cursor-pointer bg-white text-black w-15 h-7 rounded-[10px] text-[12px] hover:bg-gray-200"
          >
            Send
          </button>
        </form>
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
