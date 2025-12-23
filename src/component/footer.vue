<template>
  <footer class="relative bg-black overflow-hidden">
    <!-- Background Gradients -->
    <div class="pointer-events-none absolute inset-0">
      <!-- Left green glow -->
      <div
        class="absolute -top-40 -left-40 w-125 h-125
               bg-emerald-500/20 blur-[180px]"
      ></div>

      <!-- Right purple glow -->
      <div
        class="absolute -top-40 -right-40 w-125 h-125
               bg-purple-600/20 blur-[180px]"
      ></div>
    </div>

    <!-- Content -->
    <div class="relative max-w-7xl mx-auto px-6 pt-24 pb-10">
      <!-- Top Row -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-12 text-sm text-gray-400">
        <!-- Brand -->
        <div>
          <h3 class="text-white font-semibold mb-2">AuraMax</h3>
          <p class="text-gray-500">
            Designed to Move You
          </p>
        </div>

        <!-- Spacer -->
        <div></div>

        <!-- Links -->
        <div class="grid grid-cols-2 gap-10">
          <div>
            <h4 class="text-white mb-3">Quick Links</h4>
            <ul class="space-y-2">
              <li class="hover:text-white transition">Features</li>
              <li class="hover:text-white transition">Colors</li>
              <li class="hover:text-white transition">Contact</li>
            </ul>
          </div>

          <div>
            <h4 class="text-white mb-3">Pages</h4>
            <ul class="space-y-2">
              <li class="hover:text-white transition">Pricing</li>
              <li class="hover:text-white transition">Contact</li>
              <li class="hover:text-white transition">Terms of Use</li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Big Watermark -->
      <div class="relative mt-24 mb-10">
        <h1
          class="text-center font-extrabold tracking-widest
                 text-white/10 text-[clamp(4rem,15vw,12rem)]"
        >
          NULLMAX
        </h1>
      </div>

      <!-- Divider -->
      <div class="border-t border-white/10"></div>

      <!-- Copyright -->
      <p class="text-center text-xs text-gray-500 mt-6">
        NullMax © 2025 — All rights reserved
      </p>
    </div>
  </footer>
</template>
