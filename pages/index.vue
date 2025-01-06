<script setup lang="ts">

definePageMeta({
    layout: 'home'
})

useHead({
    title: 'Code Collab'
})

</script>

<template>
    <div class="bg-cover bg-center bg-no-repeat bg-fixed"
        style="background-image: url('/image/code1.jpg')">
        <div class="max-w-full min-h-screen bg-white/2 backdrop-blur-sm">
            <div class="flex justify-center items-center container mx-auto min-h-screen">
                <!-- Form Container -->
                <div
                    class=" drop-shadow-xl backdrop-blur-md bg-transparent/20 rounded-md w-[500px] h-[400px] shadow-lg">
                    <div class="text-center mt-5">
                        <h1 class="text-5xl font-semibold py-5 text-white">Welcome</h1>
                        <h1 class="text-5xl font-semibold text-white">To</h1>
                        <h1 class="text-5xl font-semibold py-5 text-white">Code Collab</h1>
                    </div>
                    <div class="border-b border-gray-100 pt-4 mx-5"></div>
                    <div class="mt-5 flex justify-center">
                        <NuxtLink to="/login" replace class="btn text-white">Go To Log In</NuxtLink>
                    </div>
                    <div class="text-center mt-5">
                        <NuxtLink to="/register" replace class="text-blue-600 text-sm">Sign Up</NuxtLink>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
