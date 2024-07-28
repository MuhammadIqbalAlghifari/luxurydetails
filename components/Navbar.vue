<template>
  <header
    ref="navbarRef"
    :class="[
      'fixed z-50 w-full transition-colors duration-300',
      isScrolled ? 'bg-black bg-opacity-30 backdrop-blur-md border-none' : 'bg-transparent'
    ]"
  >
    <nav
      class="flex px-5 md:px-12 lg:px-14 py-3 md:py-4 xl:px-0 xl:max-w-7xl xl:mx-auto justify-between items-center w-full text-white"
    >
      <MobileNav :open="open" @set-open="setOpen" />
      <p
        class="transition-all flex duration-300 lg:text-xl text-lg text-white"
        style="font-family: 'Clash Medium'"
      >
        LuxureDetails
      </p>
      <div
        class="justify-center md:gap-x-10 hidden md:flex items-center xl:text-base text-sm" style="font-family: 'Clash Light';"
      >
        <p
          class="cursor-pointer"
        >
          Service
        </p>
        <p
          class="cursor-pointer"
        >
          Pricing
        </p>
        <p
          class="cursor-pointer"
        >
          About
        </p>
        <p
          class="cursor-pointer"
        >
          Contact
        </p>
      </div>
      <p
        class="cursor-pointer hidden md:flex px-6 py-2 rounded-md border border-white"
        style="font-family: 'Clash Medium'"
      >
        Get a quote
      </p>
      <div class="flex relative w-8 h-6 flex-col justify-between items-center md:hidden" @click="toggleOpen">
        <span :class="['h-0.5 w-full rounded-lg transform transition duration-300 ease-in-out', open ? 'rotate-45 translate-y-2 bg-white' : 'bg-white']"></span>
        <span :class="['h-0.5 w-full rounded-lg transform transition-all duration-300 ease-in-out', open ? 'w-0 h-0' : 'bg-white w-full']"></span>
        <span :class="['h-0.5 w-full rounded-lg transform transition duration-300 ease-in-out', open ? '-rotate-45 -translate-y-3.5 bg-white' : 'bg-white']"></span>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import gsap from 'gsap'
import MobileNav from './MobileNav.vue'

const open = ref(false)
const isScrolled = ref(false)
const navbarRef = ref(null)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const setOpen = (val) => {
  open.value = val
}

const toggleOpen = () => {
  open.value = !open.value
}

onMounted(() => {
  gsap.fromTo(navbarRef.value, { opacity: 0, y: -100 }, { opacity: 1, y: 0, duration: 1.5 })
  window.addEventListener('scroll', handleScroll)
  return () => {
    window.removeEventListener('scroll', handleScroll)
  }
})

onBeforeUnmount(() => {})
</script>

<style>
.router-link-active {
  color: orange;
}
</style>
