<script setup>
import { ref } from 'vue'

const openIndex = ref(0)

const toggle = (index) => {
  openIndex.value = openIndex.value === index ? null : index
}

const faqs = [
  {
    question: "What’s the battery life like with ANC on?",
    answer: "Up to 30 hours with ANC on, and up to 40 hours with ANC off."
  },
  {
    question: "Can I use it wired and wirelessly?",
    answer: "Yes, the headphones support both wired and wireless modes."
  },
  {
    question: "Is it compatible with iOS and Android?",
    answer: "Absolutely. It works seamlessly with both iOS and Android devices."
  },
  {
    question: "Does it support multipoint Bluetooth connections?",
    answer: "Yes, you can connect to two devices at the same time."
  },
  {
    question: "How long does it take to fully charge?",
    answer: "A full charge takes approximately 2 hours."
  },
  {
    question: "What’s included in the box?",
    answer: "Headphones, charging cable, audio cable, and a carrying case."
  }
]
</script>

<template>
  <section class="bg-black min-h-screen flex items-center justify-center px-4">
    <div class="w-full max-w-3xl">
      <!-- Header -->
      <div class="text-center mb-10">
        <p class="text-sm uppercase tracking-widest text-gray-400 mb-2">
          FAQ
        </p>
        <h2 class="text-3xl md:text-4xl font-bold text-white">
          Got Questions? We’ve Got Answers.
        </h2>
      </div>

      <!-- FAQ List -->
      <div class="bg-neutral-900 rounded-2xl divide-y divide-neutral-800">
        <div
          v-for="(item, index) in faqs"
          :key="index"
          class="p-5 cursor-pointer"
          @click="toggle(index)"
        >
          <div class="flex items-center justify-between">
            <h3 class="text-white font-medium">
              {{ item.question }}
            </h3>
            <span
              class="text-white text-xl transition-transform duration-200"
              :class="openIndex === index ? 'rotate-45' : ''"
            >
              +
            </span>
          </div>

          <transition
            enter-active-class="transition duration-200 ease-out"
            enter-from-class="opacity-0 max-h-0"
            enter-to-class="opacity-100 max-h-40"
            leave-active-class="transition duration-150 ease-in"
            leave-from-class="opacity-100 max-h-40"
            leave-to-class="opacity-0 max-h-0"
          >
            <p
              v-if="openIndex === index"
              class="text-gray-400 text-sm mt-3 overflow-hidden"
            >
              {{ item.answer }}
            </p>
          </transition>
        </div>
      </div>
    </div>
  </section>
</template>