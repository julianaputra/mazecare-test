<script setup lang="ts">
interface IProps {
    value: number
    date: string
}
defineProps<IProps>()
</script>

<template>
    <div class="p-3 border border-gray-200 rounded-md mb-3 hover:border-rose-500 cursor-pointer flex transition-all justify-between"
        role="button">
        <div>
            <div class="text-teal-700 flex items-center mb-2 g-1">
                <UIcon name="ph:flask-duotone" class="w-3 h-3" />
                <p class="text-xs font-semibold">Mean Blood</p>
            </div>
            <div class="flex gap-[2px] items-end">
                <span class="text-base font-semibold" v-if="value">{{ value }}</span>
                <span class="text-sm text-gray-500">mg/dL</span>
            </div>
        </div>
        <div class="flex items-start text-gray-500">
            <p class="text-xs ">{{ date }}</p>
            <UIcon name="ph:caret-right" />
        </div>
    </div>
</template>