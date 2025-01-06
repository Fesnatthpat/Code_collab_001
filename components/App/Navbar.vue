<script setup lang="ts">
import { ref } from 'vue'
import { House } from 'lucide-vue-next'
import { SquareUser } from 'lucide-vue-next'
import { CircleUserRound } from 'lucide-vue-next'
import { Bug } from 'lucide-vue-next'
import { Briefcase } from 'lucide-vue-next'

// สร้าง state สำหรับเมนูที่ถูกเลือก
const selectedMenu = ref('home') // ค่าเริ่มต้นคือ 'home'

// ฟังก์ชันเปลี่ยนสถานะ active
const setActiveMenu = (menu: string) => {
    selectedMenu.value = menu
}
</script>

<template>
    <div class="text-white sticky top-0 z-50 backdrop:blur-md bg-black">
        <nav class="border-b border-gray-400 p-2 sm:p-3 px-4 sm:px-10 max-w-full flex justify-between items-center ">
            <div class="text-xl sm:text-3xl max-w-full w-[200px]">
                <h1 class="">Code Collab</h1>
            </div>
            <div>
                <ul class="flex gap-10 hidden lg:flex">
                    <!-- Home -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-5 py-2 transition',
                        selectedMenu === 'home' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('home')">
                        <House />
                    </li>

                    <!-- Bug -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-5 py-2 transition',
                        selectedMenu === 'bug' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('bug')">
                        <Bug />
                    </li>

                    <!-- Circle User -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-5 py-2 transition',
                        selectedMenu === 'profile' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('profile')">
                        <CircleUserRound />
                    </li>

                    <!-- Briefcase -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-5 py-2 transition',
                        selectedMenu === 'briefcase' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('briefcase')">
                        <Briefcase />
                    </li>
                </ul>
            </div>
            <div class="">
                <AppSearch />
            </div>
        </nav>
    </div>

    <div class="text-white sticky top-0 z-50 backdrop:blur-md bg-black lg:hidden">
        <nav class="border-b border-gray-400 p-3 px-10 flex justify-between items-center ">
            
            <div class="container mx-auto">
                <ul class="flex justify-center items-center  gap-x-5 sm:gap-10">
                    <!-- Home -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-4 py-2 transition',
                        selectedMenu === 'home' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('home')">
                        <House />
                    </li>

                    <!-- Bug -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-4 py-2 transition',
                        selectedMenu === 'bug' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('bug')">
                        <Bug />
                    </li>

                    <!-- Circle User -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-4 py-2 transition',
                        selectedMenu === 'profile' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('profile')">
                        <CircleUserRound />
                    </li>

                    <!-- Briefcase -->
                    <li :class="[
                        'hover:bg-gray-800 rounded-md px-4 py-2 transition',
                        selectedMenu === 'briefcase' ? 'bg-gray-800' : ''
                    ]" @click="setActiveMenu('briefcase')">
                        <Briefcase />
                    </li>
                </ul>
            </div>
        </nav>
    </div>
</template>

<style scoped></style>
