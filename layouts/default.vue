<script setup lang="ts">
import DefaultSidebar from '~/components/layouts/DefaultSidebar.vue';
import DefaultHeader from '~/components/layouts/DefaultHeader.vue';
</script>

<template>
    <div class="default-layout">
        <DefaultSidebar />
        <div>
            <DefaultHeader />
            <main class="p-4">
                <slot />
            </main>
        </div>
    </div>
</template>

<style scoped>
.default-layout {
    @apply bg-gray-100 grid min-h-screen;
    grid-template-columns: auto 1fr;
}
</style>