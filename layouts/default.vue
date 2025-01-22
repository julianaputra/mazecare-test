<script setup lang="ts">
import DefaultSidebar from '~/components/layouts/DefaultSidebar.vue';
import DefaultHeader from '~/components/layouts/DefaultHeader.vue';
</script>

<template>
    <div class="default-layout">
        <DefaultSidebar />
        <div>
            <DefaultHeader />
            <main class="default-layout__main">
                <slot />
            </main>
        </div>
    </div>
</template>

<style scoped>
.default-layout {
    @apply bg-gray-100;
    display: grid;
    grid-template-columns: auto 1fr;
    min-height: 100vh;
}

.default-layout__main {
    @apply p-4;
}
</style>