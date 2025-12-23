<script setup>
const testimonials = [
  {
    comment: 'These sound better than my studio monitors.',
    fullname: 'Beat Craft',
    username: '@beatcraft',
    avatar: 'https://i.pravatar.cc/100?img=12',
  },
  {
    comment: 'I wear them for 8 hours straight — no fatigue.',
    fullname: 'Emily L.',
    username: '@emilylondon',
    avatar: 'https://i.pravatar.cc/100?img=32',
  },
  {
    comment: 'You’ll hear songs you thought you knew, differently.',
    fullname: 'Jane T.',
    username: '@janeprod',
    avatar: 'https://i.pravatar.cc/100?img=45',
  },
]
</script>

<template>
  <div class="mx-10 my-32 flex flex-col space-y-14">
    <!-- Title -->
    <div class="text-center max-w-3xl mx-auto">
      <h4 class="text-[#6EE7BA] tracking-wide uppercase text-sm">
        Testimonials
      </h4>
      <p class="text-4xl text-white font-extrabold max-sm:text-3xl mt-3">
        Loved by Audiophiles & Creators
      </p>
      <p class="text-white/60 text-sm mt-2">
        Trusted by producers, streamers, and everyday listeners worldwide.
      </p>
    </div>

    <!-- Testimonials Grid -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div
        v-for="(item, index) in testimonials"
        :key="index"
        class="relative rounded-2xl bg-white/5 backdrop-blur p-6 text-white
               border border-white/10 hover:border-white/20 transition"
      >
        <!-- Quote Icon -->
        <div class="absolute top-4 left-4 text-white/20 text-2xl">
          *
        </div>

        <!-- Comment -->
        <p class="text-sm leading-relaxed mt-6">
          “{{ item.comment }}”
        </p>

        <!-- User -->
        <div class="flex items-center space-x-3 mt-6">
          <img
            :src="item.avatar"
            alt="Avatar"
            class="w-8 h-8 rounded-full object-cover"
          />
          <div>
            <p class="text-sm font-semibold">
              {{ item.fullname }}
            </p>
            <p class="text-xs text-white/50">
              {{ item.username }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

