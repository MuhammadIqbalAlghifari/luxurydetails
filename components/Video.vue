<template>
    <section class="w-full h-full px-5 xl:px-0 py-10 max-w-7xl mx-auto">
        <div ref="imageRef" class="relative w-full h-full flex overflow-hidden rounded-2xl shadow-lg shadow-[#121212]">
            <img src="/video.jpg" alt="" class="w-auto brightness-50 h-auto object-cover">
            <button class="flex flex-col justify-center items-center absolute z-20 lg:gap-y-5 gap-y-2.5 w-full h-full text-white lg:text-xl text-base md:text-lg" style="font-family: 'Clash Medium';">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="white" class="lg:size-20 md:size-14 size-8">
                    <path fill-rule="evenodd" d="M4.5 5.653c0-1.427 1.529-2.33 2.779-1.643l11.54 6.347c1.295.712 1.295 2.573 0 3.286L7.28 19.99c-1.25.687-2.779-.217-2.779-1.643V5.653Z" clip-rule="evenodd" />
                </svg>
                Play showreel
            </button>
        </div>
    </section>
</template>
<script setup>
import gsap from 'gsap';
import ScrollTrigger from 'gsap/dist/ScrollTrigger';

const imageRef = ref(null)

onMounted(() => {
    gsap.registerPlugin(ScrollTrigger)
    gsap.fromTo(imageRef.value, {opacity: 0}, {opacity: 1, duration: 1, delay: 0.3, scrollTrigger: {
        trigger: imageRef.value, 
        start: 'top bottom',
        end: 'center center'
    }})
})
</script>