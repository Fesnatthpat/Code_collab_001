<script setup lang="ts">
import { SearchCode } from 'lucide-vue-next'

</script>

<template>
    <div>
        <div class="flex items-center text-gray-100 bg-transparent border-b border-gray-400 shadow-md w-full px-3">
            <input type="text" placeholder="Search" class="bg-transparent w-full outline-none text-sm" />
            <SearchCode :size="35" color="white" class="text-gray-500 mr-2" />
        </div>
    </div>
</template>

<style scoped></style>