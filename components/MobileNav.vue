<template>
  <div
    :class="[
      'absolute top-0 left-0 h-screen w-screen bg-[#0a0606] transform transition-transform duration-300 ease-in-out filter drop-shadow-md',
      open ? '-translate-y-0' : '-translate-y-full'
    ]"
  >
    <div
      class="flex flex-col items-center justify-center lg:gap-y-4 gap-y-5 py-10 xl:text-lg text-base" style="font-family: 'Clash Light';"
    >
      <p
        class="text-white cursor-pointer font-bold transition-all duration-300"
        to="/"
        @click="setOpen(false)"
      >
        Service
      </p>
      <p
        class="text-white cursor-pointer font-bold transition-all duration-300"
        to="/about"
        @click="setOpen(false)"
      >
        Pricing
      </p>
      <p
        class="text-white cursor-pointer font-bold transition-all duration-300"
        to="/portfolio"
        @click="setOpen(false)"
      >
        About
      </p>
      <p
        class="text-white cursor-pointer font-bold transition-all duration-300"
        to="/news"
        @click="setOpen(false)"
      >
        Contact
      </p>
      <p
        class="cursor-pointer px-6 py-2 rounded-md border text-white border-white"
        style="font-family: 'Clash Medium'"
      >
        Get a quote
      </p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  open: Boolean
})

const emit = defineEmits(['set-open'])

const setOpen = (val) => {
  emit('set-open', val)
}
</script>
