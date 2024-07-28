<template>
    <img ref="imageHero" src="/hero.jpg" class="w-full md:h-full h-screen relative pt-40 z-10 object-cover">
    <article ref="textHero"class="w-full h-screen flex px-5 xl:px-0 flex-col text-white z-20 absolute justify-start top-0 pt-24 items-center lg:gap-y-5 gap-y-2.5">
        <h1 class="lg:text-8xl sm:text-4xl text-3xl md:text-6xl text-center" style="font-family: 'Clash Medium';">Luxury car detailing</h1>
        <p class="lg:text-xl text-base md:text-lg max-w-xl text-[#e1e1e1] leading-normal text-center" style="font-family: 'Clash Regular';">Experience the prestige of a professionally detailed car, radiating elegance and refinement at every turn.</p>
        <button class="flex justify-center items-center gap-x-5">
            <p class="lg:text-xl text-base md:text-lg" style="font-family: 'Clash Medium';">Let's Connect</p>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 19.5 15-15m0 0H8.25m11.25 0v11.25" />
            </svg>
        </button>
    </article>
</template>
<script setup>
import gsap from 'gsap';

const imageHero = ref(null)
const textHero = ref(null)

onMounted(() => {
    gsap.fromTo(imageHero.value, {opacity: 0}, {opacity: 1, ease: 'power3.out', duration: 1.5})
    gsap.fromTo(textHero.value.children, {opacity: 0}, {opacity: 1, ease: 'power3.out', duration: 1, stagger: 0.5})
})

</script>