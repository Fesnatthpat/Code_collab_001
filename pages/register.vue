<script setup lang="ts">
import { ref } from 'vue';

const email = ref('');
const password = ref('');

const handleSubmit = async () => {
    console.log('Email:', email.value);
    console.log('Password:', password.value);
};

definePageMeta({
    layout: 'auth',
});
</script>

<template>
    <div class="bg-black container mx-auto flex justify-center items-center max-w-full min-h-screen">
        <div class="border border-gray-500 w-[500px] p-10">
            <form @submit.prevent="handleSubmit" class="">
                <h1 class="text-white text-5xl text-center">Sign Up</h1>

                <!-- Input Fields -->
                <AppFormInput v-model="email" label="Full Name" placeholder="Full Name..." type="text" />
                <AppFormInput v-model="email" label="Email" placeholder="Email..." type="text" />
                <AppFormInput v-model="password" label="Password" placeholder="Password..." type="password" />
                <AppFormInput v-model="password" label="Confirm Password" placeholder="Confirm Password..."
                    type="password" />

                <!-- Submit Button -->
                <div class="mt-5 text-center">
                    <NuxtLink to="/" class="btn">Sign Up</NuxtLink>
                </div>
            </form>
        </div>
    </div>
</template>

<style scoped></style>
