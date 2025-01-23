<script setup lang="ts">
interface IProps {
    name: string
    value: number | null
    unit: string
}

defineProps<IProps>()
</script>

<template>
    <div class="p-3 border border-gray-200 rounded-md mb-3 flex justify-between items-center transition-all hover:border-red-500" role="button">
        <div>
            <div class="text-teal-700 flex items-center mb-2 gap-1">
                <UIcon name="ph:flask-duotone" class="w-3 h-3" />
                <p class="text-xs font-semibold">{{ name }}</p>
            </div>
            <div class="flex items-end gap-[2px]">
                <span class="text-base font-semibold" v-if="value">{{ value }}</span>
                <span class="text-sm text-gray-500" v-if="unit">{{ unit }}</span>
            </div>
        </div>
        <UIcon name="ph:caret-right" />
    </div>
</template>
