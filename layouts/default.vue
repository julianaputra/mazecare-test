<script setup lang="ts">
import DefaultSidebar from '~/components/layouts/DefaultSidebar.vue';
import DefaultHeader from '~/components/layouts/DefaultHeader.vue';
</script>

<template>
    <div class="default-layout">
        <DefaultSidebar />
        <div>
            <DefaultHeader />
            <main>
                <slot />
            </main>
        </div>
    </div>
</template>

  <style scoped>
.default-layout {
    display: grid;
    grid-template-columns: auto 1fr;
    min-height: 100vh;
}
</style>