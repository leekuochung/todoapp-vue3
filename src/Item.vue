<script setup>
import { computed } from "vue"

const props = defineProps({
    device: {
        type: Object,
        required: true,
    },
})

const emits = defineEmits(["remove-auo-item"])

const remove = () => {
    emits("remove-auo-item", props.device.id)
}

const todo_id = computed(() => `todo_id_${props.device.id}`)
</script>

<template>
    <li class="flex items-center justify-between py-6 border-b">
        
        <div class="flex items-center gap-3">
            <input type="checkbox" :id="todo_id" class="checkbox" v-model="device.isDelete" />
            <label :for="todo_id" class="text-xl cursor-pointer">
                <span v-if="device.isDelete" style="text-decoration: line-through;">{{ device.title }}</span>
                <span v-else>{{ device.title }}</span>
            </label>
        </div>
        <button @click="remove" class="p-2 hover:text-white hover:bg-neutral">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0"
                />
            </svg>
        </button>
    </li>
</template>