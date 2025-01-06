<script setup lang="ts">
import { ref } from 'vue'
import { Images, X } from 'lucide-vue-next'

const content = ref('')
const code = ref('')

// ตัวแปรสำหรับอ้างอิง input file
const fileInput = ref<HTMLInputElement | null>(null)

// ตัวแปรสำหรับเก็บรูปภาพที่อัปโหลด
const images = ref<string[]>([])

// ตัวแปรสำหรับควบคุมการแสดงรูปที่ซ่อน
const showAllImages = ref(false)

// ฟังก์ชันสำหรับเปิดหน้าต่างเลือกไฟล์
const handleFileClick = () => {
    fileInput.value?.click()
}

// ฟังก์ชันสำหรับจัดการการเปลี่ยนไฟล์
const handleFileChange = (event: Event) => {
    const target = event.target as HTMLInputElement
    const files = target.files

    if (files) {
        for (let i = 0; i < files.length; i++) {
            const file = files[ i ]
            const imageUrl = URL.createObjectURL(file)
            images.value.push(imageUrl)
        }
    }
}

// ฟังก์ชันสำหรับลบรูปภาพ
const removeImage = (index: number) => {
    images.value.splice(index, 1)
}

// ฟังก์ชันสำหรับเปลี่ยนสถานะการแสดงรูปที่ซ่อน
const toggleShowAllImages = () => {
    showAllImages.value = !showAllImages.value
}
</script>

<template>
    <div class="min-h-screen">
        <div class="flex justify-center items-start mx-5 mt-5">
            <div class="border-b w-[500px]">
                <h1 class="text-center text-2xl">Create Post</h1>
                <form @submit.prevent="" class="p-5">
                    <AppFormInput v-model="content" label="Content" placeholder="Content" type="text" />
                    <AppFormInput v-model="code" class="mt-2" label="Code" placeholder="Code" type="text" />

                    <!-- Hidden file input -->
                    <input ref="fileInput" type="file" class="hidden" multiple @change="handleFileChange" />

                    <!-- Icon to trigger file input -->
                    <div class="cursor-pointer flex justify-center items-center mt-3" @click="handleFileClick">
                        <Images class="text-white w-8 h-8" />
                    </div>

                    <!-- Display images -->
                    <div class="mt-4 max-h-[400px] h-full overflow-y-auto">
                        <!-- When there's a single image -->
                        <div v-if="images.length === 1"
                            class="relative w-full h-[400px] rounded-md overflow-hidden border border-gray-300">
                            <img :src="images[ 0 ]" alt="Uploaded" class=" object-contain w-full h-full" />
                            <div class="absolute top-2 right-2 btn btn-sm bg-red-500 rounded-full text-white p-1 cursor-pointer"
                                @click="removeImage(0)">
                                <X class="w-5 h-5" />
                            </div>
                        </div>

                        <!-- When there are multiple images -->
                        <div v-else class="flex flex-wrap gap-2">
                            <template v-for="(image, index) in (showAllImages ? images : images.slice(0, 5))"
                                :key="index">
                                <div class="relative w-24 h-24 rounded-md overflow-hidden border border-gray-300 group">
                                    <img :src="image" alt="Uploaded" class="object-cover w-full h-full" />
                                    <div class="absolute top-1 right-1 btn btn-sm btn-error rounded-full text-white p-1  cursor-pointer opacity-0 group-hover:opacity-100 transition"
                                        @click="removeImage(index)">
                                        <X class="w-5 h-5" />
                                    </div>
                                </div>
                            </template>

                            <!-- Button to toggle showing more images -->
                            <div v-if="images.length > 5" class="w-24 h-24 flex items-center justify-center">
                                <button class="text-blue-500 font-semibold underline"
                                    @click.prevent="toggleShowAllImages">
                                    {{ showAllImages ? 'Hide...' : '+' + (images.length - 5) + '...' }}
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="text-center   mt-5">
                        <button class="btn max-w-full w-5/6 sm:w-[400px]  btn-success">Post</button>
                    </div>
                </form>
            </div>
        </div>

        <div class="m-5">
            <div class="border container mx-auto w-[700px] max-w-full min-h-full p-2 mt-10">
                <div class="container mx-auto">
                    <div class="avatar placeholder flex justify-start items-center gap-2">
                        <div class="bg-neutral text-neutral-content w-8 rounded-full">
                            <span class="text-sm">SY</span>
                        </div>
                        <p>Lorem ipsum dolor sit amet.</p>
                    </div>


                </div>
            </div>
        </div>

    </div>




</template>
