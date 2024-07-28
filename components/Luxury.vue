<template>
    <section class="w-full h-full px-5 xl:px-0 py-10 max-w-7xl mx-auto">
        <div class="relative w-full h-full flex overflow-hidden rounded-2xl shadow-lg shadow-[#121212]">
            <img ref="imageRef"src="/lancer.jpg" alt="" class="w-auto scale-x-[-1] lg:brightness-90 md:brightness-75 brightness-50 h-auto object-cover">
            <div ref="titleRef"class="flex flex-col lg:justify-start justify-center lg:items-start items-center lg:p-20 md:p-10 p-5 absolute z-20 lg:gap-y-5 gap-y-2.5 w-full h-full text-white" style="font-family: 'Clash Medium';">
                <h1 class="lg:text-5xl lg:text-start text-center text-xl md:text-3xl max-w-md leading-tight">Book your luxury car detailing today</h1>
                <p class="lg:text-base md:text-sm text-xs text-[#cccccc] lg:text-start text-center max-w-xs">Click the link bellow. Fill out the details and we’ll get back to you in less than 24 hours.</p>
                <button class="flex justify-center items-center gap-x-5 text-white">
                    <p class="lg:text-xl text-base md:text-lg" style="font-family: 'Clash Medium';">Get a quote now</p>
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 19.5 15-15m0 0H8.25m11.25 0v11.25" />
                    </svg>
                </button>
            </div>
        </div>
    </section>
</template>
<script setup>

import gsap from 'gsap';
import ScrollTrigger from 'gsap/dist/ScrollTrigger';

const imageRef = ref(null)
const titleRef = ref(null)

onMounted(() => {
    gsap.registerPlugin(ScrollTrigger)
    gsap.fromTo(imageRef.value, {opacity: 0}, {opacity: 1, duration: 1, delay: 0.3, scrollTrigger: {
        trigger: imageRef.value, 
        start: 'top bottom',
        end: 'center center'
    }})
    titleRef.value.childNodes.forEach(child => {
        gsap.fromTo(child, {opacity: 0, y: 10}, {opacity: 1, y: 0, duration: 1, delay: 0.3, scrollTrigger: {
            trigger: child, 
            start: 'top bottom',
            end: 'center center'
        }})
    })
})

</script>