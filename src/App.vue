<script setup>
    import DeviceItem from "@/Item.vue"
    import { v4 as uuidv4 } from "uuid"
    import { ref, reactive } from "vue"
    const device = ref("")
    const devices = reactive([])
    const StorageKey = "AUO-Device-List"

    const addDevice = () => {
        if (device.value !== "") {            
            const item = {
                id: uuidv4(),
                isDelete: false,
                title: device.value,
            }
            devices.unshift(item)
            device.value = ""
        }
    }

    const removeItem = (id) => {
        const index = devices.findIndex((device) => {
            return device.id === id
        })

        devices.splice(index, 1)
    }
</script>

<template>
    <header class="m-2">
        <h1 class="text-6xl font-thin select-none">leekuochung -- TODO!</h1>
        <div class="font-semibold select-none text-neutral-600">simple and studid todo app</div>
    </header>
    <form class="px-10 py-12 bg-white shadow-sm">
        <section class="flex">
            <input v-model="device" type="text" placeholder="做點重要的事吧..." class="w-full text-2xl focus:outline-none input-lg input input-bordered" />
            <button @click.prevent="addDevice" class="text-xl btn-lg btn btn-neutral">新增</button>
        </section>
    </form>

    <section>
        <ul>
            <DeviceItem
                @remove-auo-item="removeItem"
                v-for="d in devices"
                :device="d"
            />
        </ul>
    </section>
</template>

<style scoped>
    
</style>
