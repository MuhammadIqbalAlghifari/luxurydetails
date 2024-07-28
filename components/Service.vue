<template>
    <section class="py-10 overflow-hidden max-w-7xl px-5 xl:px-0 mx-auto w-full h-full flex flex-col gap-y-10 lg:gap-y-0 lg:flex-row lg:justify-between justify-center items-stretch">
        <div ref="heroLeft" class="flex-col flex justify-center lg:items-start items-center lg:max-w-lg w-full">
            <h1 class="text-white lg:text-5xl lg:text-start text-center text-3xl md:text-4xl" style="font-family: 'Clash Medium';">We will take good care of your car</h1>
            <img src="/bmw.jpg" class="w-auto h-auto object-cover">
        </div>
        <hr ref="hrItem"class="lg:h-auto lg:w-[0.5px] hidden lg:flex bg-white"/>
        <div ref="heroRight" class="flex-col flex h-auto w-full justify-between lg:items-start gap-y-5 lg:gap-y-0 items-center lg:max-w-md">
            <div class="flex-col flex lg:gap-y-5 gap-y-2.5 justify-center lg:items-start items-center">
                <div class="text-white flex justify-start items-center gap-x-5 text-2xl" style="font-family: 'Clash Medium';">
                    <!-- SVG Here -->
                    <span class="text-center lg:text-start">Precise work</span>
                </div>
                <p class="text-[#cccccc] text-center lg:text-start md:text-base text-sm" style="font-family: 'Clash Medium';">We uphold the highest standards of professionalism when servicing your vehicles.</p>
            </div>
            <hr class="h-[0.5px] w-full bg-white"/>
            <div class="flex-col flex lg:gap-y-5 gap-y-2.5 justify-center lg:items-start items-center">
                <div class="text-white flex justify-start items-center gap-x-5 text-2xl" style="font-family: 'Clash Medium';">
                    <!-- SVG Here -->
                    <span class="text-center lg:text-start">Premium Products and Services</span>
                </div>
                <p class="text-[#cccccc] text-center lg:text-start md:text-base text-sm" style="font-family: 'Clash Medium';">Ensure your car's longevity with a periodic exterior protection treatment.</p>
            </div>
            <hr class="h-[0.5px] w-full bg-white"/>
            <div class="flex-col flex lg:gap-y-5 gap-y-2.5 justify-center lg:items-start items-center">
                <div class="text-white flex justify-start items-center gap-x-5 text-2xl" style="font-family: 'Clash Medium';">
                    <!-- SVG Here -->
                    <span class="text-center lg:text-start">High-Level Security and Privacy</span>
                </div>
                <p class="text-[#cccccc] text-center lg:text-start md:text-base text-sm" style="font-family: 'Clash Medium';">We understand the importance of privacy and security for their our clientele.</p>
            </div>
            <button class="flex justify-center items-center lg:gap-x-5 gap-x-2.5 text-white">
                <p class="lg:text-xl text-base md:text-lg" style="font-family: 'Clash Medium';">Get a quote now</p>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
                    <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 19.5 15-15m0 0H8.25m11.25 0v11.25" />
                </svg>
            </button>
        </div>
    </section>
</template>
<script setup>

import gsap from 'gsap';
import ScrollTrigger from 'gsap/dist/ScrollTrigger';

const heroLeft = ref(null)
const hrItem = ref(null)
const heroRight = ref(null)

const animateOnScroll = (element, {opacity, x, y}) => {
    gsap.registerPlugin(ScrollTrigger)
    gsap.fromTo(element, {opacity, x, y}, {
        opacity: 1,
        duration: 1,
        delay: 0.2,
        stagger: 0.3,
        x: 0,
        y: 0,
        ease: 'power3.out',
        scrollTrigger: {
            trigger: element,
            start: 'top bottom',
            end: 'center center',
        }
    })
}

const animateOnDekstop = () => {
    animateOnScroll(heroLeft.value, {opacity: 0, x: -100})
    animateOnScroll(hrItem.value, {opacity: 0})
    animateOnScroll(heroRight.value.children, {opacity: 0, x: 100})
}

const animateOnMobile = () => {
    animateOnScroll(heroLeft.value, {opacity: 0, y: 50})
    animateOnScroll(hrItem.value, {opacity: 0})
    heroRight.value.childNodes.forEach(child => {
        animateOnScroll(child, {opacity: 0, y: 50})
    })
}

onMounted(() => {

    const isDekstop = window.matchMedia("(min-width: 1024px)").matches

    isDekstop ? animateOnDekstop() : animateOnMobile()

})

</script>
<style>
    
</style>