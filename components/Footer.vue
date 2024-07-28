<template>
    <footer ref="titleRef" class="max-w-screen-xl mx-auto flex px-5 lg:py-20 py-8 md:py-14 md:justify-between flex-col gap-y-10 items-stretch h-full w-full">
        <div class="flex md:justify-between flex-col md:flex-row gap-y-5 md:gap-y-0 md:items-stretch items-center h-full w-full">
            <div class="flex flex-col max-w-sm justify-between gap-y-2 md:gap-y-0 items-stretch h-auto w-full">
                <div class="flex flex-col justify-center gap-y-2.5 xl:gap-y-5 lg:items-start items-center">
                    <h1 class="text-xl text-center md:text-start text-white" style="font-family: 'Clash Medium';">LuxureDetails</h1>
                    <p class="text-[#999999] text-center md:text-start max-w-[22rem] md:text-base text-sm" style="font-family: 'Clash Regular';">Experience the prestige of a professionally detailed car, radiating elegance and refinement at every turn.</p>
                </div>
            </div>
            <div class="flex flex-col md:flex-row justify-between gap-y-5 md:gap-y-0 md:items-start items-center w-full max-w-xl" style="font-family: 'Clash Medium';">
                <div class="flex flex-col justify-between md:items-start items-center h-auto md:text-base text-sm gap-y-2.5 lg:gap-y-5">
                    <h1 class="text-[#999999]">Websites</h1>
                    <p class="text-white">Services</p>
                    <p class="text-white">Pricing</p>
                    <p class="text-white">About</p>
                </div>
                <div class="flex flex-col justify-between md:items-start items-center h-auto md:text-base text-sm gap-y-2.5 lg:gap-y-5">
                    <h1 class="text-[#999999]">Contact</h1>
                    <p class="text-white">Get a quote</p>
                    <p class="text-white">Contact form</p>
                    <p class="text-white">Email us</p>
                </div>
                <div class="flex flex-col justify-between md:items-start items-center h-auto md:text-base text-sm gap-y-2.5 lg:gap-y-5">
                    <h1 class="text-[#999999]">Social media</h1>
                    <p class="text-white">Facebook</p>
                    <p class="text-white">Instagram</p>
                    <p class="text-white">Twitter</p>
                    <p class="text-white">Youtube</p>
                </div>
            </div>
        </div>
        <hr class="w-full h-[0.5px] bg-white">
        <div class="flex flex-col md:flex-row gap-y-2.5 justify-between items-center w-full md:text-base text-sm" style="font-family: 'Clash Medium';">
            <p class="text-white xl:text-lg lg:text-sm text-start">LuxureDetails © {{ currentYear }}</p>
            <div class="flex justify-center flex-col md:flex-row items-center gap-y-5 md:gap-y-0 gap-x-10 text-white">
                <p>Cookie policy</p>
                <p>Terms of service</p>
                <p>Privacy policy</p>
            </div>
        </div>
    </footer>
</template>

<script setup>
import gsap from 'gsap';
import ScrollTrigger from 'gsap/dist/ScrollTrigger';

const currentYear = new Date().getFullYear()
const titleRef = ref(null)

onMounted(() => {
    gsap.registerPlugin(ScrollTrigger)
    titleRef.value.childNodes.forEach(child => {
        gsap.fromTo(child, {opacity: 0, y: 10}, {opacity: 1, y: 0, duration: 1, delay: 0.3, scrollTrigger: {
            trigger: child, 
            start: 'top bottom',
            end: 'center center'
        }})
    })
})

</script>
