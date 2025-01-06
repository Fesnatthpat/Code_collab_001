<script setup lang="ts">
defineProps<{
    label: string;
    placeholder: string;
    type: string;
    modelValue: string | number;
}>();

const emit = defineEmits([ 'update:modelValue' ]);

const updateValue = (event: Event) => {
    const target = event.target as HTMLInputElement;
    emit('update:modelValue', target.type === 'file' ? target.files : target.value);
};
</script>

<template>
    <div>
        <!-- Label -->
        <label class="ml-3">{{ label }}</label>

        <!-- Input -->
        <label class="input input-bordered bg-transparent  flex items-center gap-2">
            <!-- Non-file input -->
            <input v-bind="$attrs" :value="modelValue" @input="updateValue" v-if="type !== 'file'" :type="type"
                :placeholder="placeholder" class="grow  border-b " />
            <!-- File input -->
            <input type="file" class="grow" v-else @change="updateValue" />
        </label>
    </div>
</template>

<style scoped></style>
