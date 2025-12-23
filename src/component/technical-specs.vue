<script setup>
const specs = [
  { label: 'Driver Size', value: '40mm Titanium-Coated Dynamic Drivers' },
  { label: 'Frequency Response', value: '20Hz – 40kHz' },
  { label: 'Impedance', value: '32Ω' },
  { label: 'Bluetooth Version', value: '5.3 with Multipoint Connectivity' },
  { label: 'Audio Codecs', value: 'SBC, AAC, aptX™, aptX Adaptive™' },
  { label: 'Noise Cancellation', value: 'Hybrid Active Noise Cancellation (up to 40dB)' },
  { label: 'Battery Life', value: 'Up to 40h (ANC off), 30h (ANC on)' },
  { label: 'Charging Time', value: '≈ 1.5 hours (Fast Charge)' },
  { label: 'Microphones', value: 'Dual Beamforming Mics with ENC' },
  { label: 'Weight', value: '260g' },
]
</script>

<template>
  <div class="mx-10 my-20 flex flex-col space-y-8">
    <!-- Title -->
    <div class="pt-10 text-left">
      <h4 class="text-[#6EE7BA]">Technical Specifications</h4>
      <p class="text-4xl text-white font-extrabold max-sm:text-3xl mt-3">
        Engineered to Perform.
      </p>
      <p class="text-white/60 text-sm">
        All the details that make the NullMax exceptional.
      </p>
    </div>

    <!-- Specs List -->
    <div class="divide-y divide-white/10">
      <div
        v-for="spec in specs"
        :key="spec.label"
        class="grid grid-cols-2 py-4 max-sm:grid-cols-1 max-sm:gap-1"
      >
        <p class="text-white/70 text-sm">
          {{ spec.label }}
        </p>
        <p class="text-white text-sm text-left max-sm:text-left">
          {{ spec.value }}
        </p>
      </div>
    </div>
  </div>
</template>
