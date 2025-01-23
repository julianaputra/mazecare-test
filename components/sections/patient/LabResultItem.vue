<script setup lang="ts">
interface IProps {
    name: string
    value: number | null
    unit: string
}
defineProps<IProps>()
</script>

<template>
    <div class="item" role="button">
        <div>
            <div class="item__header">
                <UIcon name="ph:flask-duotone" class="item__icon" />
                <p class="item__name">{{ name }}</p>
            </div>
            <div class="item__body">
                <span class="item__value" v-if="value">{{ value }}</span>
                <span class="item__unit" v-if="unit">{{ unit }}</span>
            </div>
        </div>
        <UIcon name="ph:caret-right" />
    </div>
</template>

<style scoped>
.item {
    @apply p-3 border border-gray-200 rounded-md mb-3 grid;
    grid-template-columns: 1fr auto;
    align-items: center;
    cursor: pointer;
    transition: all .2s ease;
}
.item:hover {
    @apply border-rose-500;
}

.item__header {
    @apply text-teal-700 flex items-center mb-2;
    gap: 4px;
}

.item__name {
    @apply text-xs font-semibold;
}

.item__icon {
    @apply w-3 h-3;
}

.item__value {
    @apply text-base font-semibold;
}

.item__unit {
    @apply text-sm text-gray-500;
}

.item__body {
    @apply flex;
    align-items: end;
    gap: 2px;
}
</style>