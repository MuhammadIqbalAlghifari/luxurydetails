<template>
  <div class="bg-black">
    <Navbar/>
    <Hero/>
    <Detail/>
    <Video/>
    <Service/>
    <Luxury/>
    <Footer/>
  </div>
</template>

<script setup>
import './assets/font.css'
import Lenis from 'lenis';
useHead({
  title: 'Luxury Car',
  meta: [
    {name: 'description', content: 'nuxt.js'}
  ]
})

onMounted(() => {
  const lenis = new Lenis()

  function raf(time) {
    lenis.raf(time)
    requestAnimationFrame(raf)
  }

  requestAnimationFrame(raf)
})
</script>
