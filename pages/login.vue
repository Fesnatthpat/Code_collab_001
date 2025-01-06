<script setup lang="ts">

import { Github } from 'lucide-vue-next'

const email = ref('')
const password = ref('')

const handlesubmit = async () => {
    console.log('Email:', email.value)
    console.log('Password:', password.value)
}

definePageMeta({
    layout: 'auth'
})
</script>

<template>
    <div class="bg-black container mx-auto flex justify-center items-center  max-w-full min-h-screen">
        <div class="border  border-gray-500 w-[500px] p-10">
            <form @submit.prevent="handlesubmit" class="">
                <h1 class="text-white text-5xl text-center">Log In</h1>
                <!-- btn-login -->
                <div class="flex justify-center items-center gap-x-5 mt-10">
                    <button class="btn">
                        <Github />
                        <p>Sign in with a Github</p>
                    </button>
                    <button class="btn">
                        <img src="public\image\icons8-google-48.png" class="w-[25px]">
                        <p>Sign in with a Google</p>
                    </button>
                </div>
                <div class="mt-10">
                    <AppFormInput v-model="email" label="Email" placeholder="Email..." type="text" />
                    <AppFormInput v-model="password" label="Password" placeholder="Password..." type="password" />
                </div>
                <div class="mt-5 text-center">
                    <NuxtLink to="/Add-Posts/feed" class="btn">Log In</NuxtLink>
                </div>
            </form>
        </div>
    </div>
</template>

<style scoped></style>