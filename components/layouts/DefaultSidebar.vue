<script setup lang="ts">
const navItems = ref([
    {
        id: 1,
        name: 'Home',
        to: '/',
        icon: 'ph:house-duotone'
    },
    {
        id: 2,
        name: 'Palette',
        to: '/palette',
        icon: 'ph:palette-duotone'
    },
    {
        id: 3,
        name: 'Folder',
        to: '/folder',
        icon: 'ph:folder-duotone'
    },
    {
        id: 4,
        name: 'Calendar',
        to: '/calendar',
        icon: 'ph:calendar-duotone'
    },
    {
        id: 5,
        name: 'File',
        to: '/file',
        icon: 'ph:file-duotone'
    },
    {
        id: 6,
        name: 'Chart',
        to: '/chart',
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
    @apply bg-gray-50 border-e border-gray-200 grid h-screen sticky top-0;
    grid-template-rows: auto 1fr;
}

.default-sidebar__logo {
    @apply border-b border-gray-200 flex items-center justify-center h-[62px];
}

.default-sidebar__wrapper {
    display: grid;
    grid-template-rows: 1fr auto;
}

.default-sidebar__nav-item {
    @apply px-4 py-2 rounded-md flex transition-all;
}

.default-sidebar__nav-item.router-link-active {
    @apply bg-rose-500 text-white;
}

.default-sidebar__nav-item:hover {
    @apply bg-rose-400 text-white;
}

.default-sidebar__nav-icon {
    @apply w-6 h-6;
}

.default-sidebar__nav {
    @apply flex flex-col gap-3;
}

.default-sidebar__actions {
    @apply flex flex-col gap-3;
}
</style>