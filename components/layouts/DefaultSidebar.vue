<script setup lang="ts">
const navItems = ref([
    {
        id: 1,
        name: 'Home',
        to: { name: 'index' },
        icon: 'ph:house-duotone'
    },
    {
        id: 2,
        name: 'Palette',
        to: { name: 'index' },
        icon: 'ph:palette-duotone'
    },
    {
        id: 3,
        name: 'Folder',
        to: { name: 'index' },
        icon: 'ph:folder-duotone'
    },
    {
        id: 4,
        name: 'Calendar',
        to: { name: 'index' },
        icon: 'ph:calendar-duotone'
    },
    {
        id: 5,
        name: 'File',
        to: { name: 'index' },
        icon: 'ph:file-duotone'
    },
    {
        id: 6,
        name: 'Chart',
        to: { name: 'index' },
        icon: 'ph:chart-bar-duotone'
    },
])
</script>

<template>
    <aside class="default-sidebar">
        <div class="default-sidebar__logo">
            <UIcon name="ph:diamonds-four-duotone" class="w-7 h-7" />
        </div>
        <div class="default-sidebar__wrapper p-3">
            <nav class="default-sidebar__nav">
                <NuxtLink class="default-sidebar__nav-item" v-for="navItem in navItems" :key="navItem.id"
                    :to="navItem.to">
                    <UIcon :name="navItem.icon" class="default-sidebar__nav-icon" />
                </NuxtLink>
            </nav>
            <div class="default-sidebar__actions">
                <button class="default-sidebar__nav-item">
                    <UIcon name="ph:arrow-circle-right-duotone" class="default-sidebar__nav-icon" />
                </button>
                <button class="default-sidebar__nav-item">
                    <UIcon name="ph:gear-duotone" class="default-sidebar__nav-icon" />
                </button>
            </div>
        </div>
    </aside>
</template>

<style scoped>
.default-sidebar {
    @apply bg-gray-50 border-e border-gray-200;
    display: grid;
    grid-template-rows: auto 1fr;
}

.default-sidebar__logo {
    @apply border-b border-gray-200;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 62px;
}

.default-sidebar__wrapper {
    display: grid;
    grid-template-rows: 1fr auto;
}

.default-sidebar__nav-item {
    @apply px-4 py-2 rounded-md;
    display: flex;
    transition: all .2s ease;
}

.default-sidebar__nav-item:hover {
    @apply bg-red-500;
}

.default-sidebar__nav-icon {
    @apply w-6 h-6;
}

.default-sidebar__nav {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.default-sidebar__actions {
    display: flex;
    flex-direction: column;
    gap: 12px;
}
</style>