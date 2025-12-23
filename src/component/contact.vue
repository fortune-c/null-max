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
  <div
    class="mx-5 md:mx-10 flex flex-col items-center my-20"
    id="contact"
  >
    <Transition name="slide-left">
      <div
        v-if="showComponent"
        class="pt-10 w-full max-w-2xl text-center"
      >
        <h4 class="text-[#6EE7BA]">CONTACT</h4>

        <p class="text-3xl md:text-4xl text-white font-extrabold mt-2">
          We’d love to hear from you
        </p>

        <form class="text-left mt-6 space-y-4">
          <!-- Name -->
          <div>
            <label class="text-white text-sm">Name</label>
            <input
              type="text"
              placeholder="Your Name"
              class="w-full h-10 rounded-lg bg-[#0D0D0D] border border-gray-600 text-white text-sm px-3"
            />
          </div>

          <!-- Email -->
          <div>
            <label class="text-white text-sm">Email</label>
            <input
              type="email"
              placeholder="you@example.com"
              class="w-full h-10 rounded-lg bg-[#0D0D0D] border border-gray-600 text-white text-sm px-3"
            />
          </div>

          <!-- Message -->
          <div>
            <label class="text-white text-sm">Message</label>
            <textarea
              rows="4"
              placeholder="Tell us a bit about your request"
              class="w-full rounded-lg bg-[#0D0D0D] border border-gray-600 text-white text-sm px-3 py-2"
            ></textarea>
          </div>

          <!-- Button -->
          <button
            type="submit"
            class="mt-4 bg-white text-black px-6 py-2 rounded-lg text-sm hover:bg-gray-200 transition"
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
