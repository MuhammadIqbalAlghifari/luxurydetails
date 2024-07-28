<template>
    <main class="w-full px-5 xl:px-0 h-full text-white relative py-10 max-w-7xl mx-auto lg:gap-y-5 gap-y-2.5 z-10 flex flex-col justify-center lg:items-start items-center">
        <h1 ref="titleOne" class="lg:text-xl text-base md:text-lg text-[#999999]" style="font-family: 'Clash Medium';">Luxury car detailing</h1>
        <hr ref="hrItem"class="w-full h-0.5 bg-white"/>
        <div ref="titleTwo"class="flex flex-col gap-y-2.5 lg:flex-row justify-between items-center w-full py-10">
            <h1 style="font-family: 'Clash Medium';" class="text-white lg:text-5xl lg:text-start text-center text-3xl md:text-4xl">Love in Every Detail</h1>
            <p style="font-family: 'Clash Regular';" class="text-[#999999] lg:text-start text-center max-w-lg lg:text-xl text-base md:text-lg">Immerse yourself in luxury with our bespoke detailing packages tailored to your car's unique needs.</p>
        </div>
        <div class="flex flex-col lg:flex-row lg:justify-between justify-center gap-y-5 items-center lg:gap-y-0 lg:gap-x-10 w-full h-full">
            <div ref="cardItem" class="flex-col flex justify-center lg:items-start items-center lg:gap-y-5 gap-y-2.5 text-white w-auto h-auto" v-for="(car, index) in carData" :key="index">
                <img :src='car.image' alt="" class="w-auto h-auto object-cover object-center rounded-xl">
                <h1 class="lg:text-2xl md:text-xl text-lg text-white" style="font-family: 'Clash Medium';">{{ car.title }}</h1>
                <p style="font-family: 'Clash Regular';" class="text-[#999999] lg:text-base text-sm text-center lg:text-start">{{ car.desc }}</p>
                <button class="flex justify-start items-center gap-x-5">
                    <p style="font-family: 'Clash Regular';" class="text-white lg:text-base text-sm">Learn more</p>
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3" />
                    </svg>
                </button>
            </div>
        </div>
    </main>
</template>
<script setup>

import gsap from 'gsap';
import ScrollTrigger from 'gsap/dist/ScrollTrigger';

const titleOne = ref(null)
const hrItem = ref(null)
const titleTwo = ref(null)
const cardItem = ref([])

onMounted(() => {
    gsap.registerPlugin(ScrollTrigger)
    gsap.fromTo(titleOne.value, {opacity: 0, y: 50}, {opacity: 1, y: 0, duration: 1, delay: 0.2, scrollTrigger: {
        trigger: titleOne.value,
        start: 'top bottom',
        end: 'center center'
    }})
    gsap.fromTo(hrItem.value, {opacity: 0, y: 50}, {opacity: 1, y: 0, duration: 1, delay: 0.2, scrollTrigger: {
        trigger: hrItem.value,
        start: 'top bottom',
        end: 'center center'
    }})
    gsap.fromTo(titleTwo.value, {opacity: 0, y: 50}, {opacity: 1, y: 0, duration: 1, delay: 0.2, scrollTrigger: {
        trigger: titleTwo.value,
        start: 'top bottom',
        end: 'center center'
    }})
    cardItem.value.forEach(child => {
        gsap.fromTo(child, {opacity: 0, y: 50}, {opacity: 1, y: 0, duration: 1, delay: 0.2, scrollTrigger: {
            trigger: child,
            start: 'top bottom',
            end: 'center center'
        }})
    })
})

const carData = [
    {
        image: '/elegant.jpg',
        title: 'Entry Level Detail',
        desc: 'Treat your luxury car to a thorough hand wash and wax application.',
    },
    {
        image: '/porche.jpg',
        title: 'Maintenance detail',
        desc: "Ensure your car's longevity with a periodic exterior protection treatment.",
    },
    {
        image: '/detail.jpg',
        title: 'Full detail',
        desc: 'Pamper your vehicle with a complete treatment, leaving no detail overlooked.',
    }
]

</script>
<style>
    
</style>