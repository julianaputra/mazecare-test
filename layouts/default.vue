<script setup lang="ts">
import DefaultSidebar from '~/components/layouts/DefaultSidebar.vue';
import DefaultHeader from '~/components/layouts/DefaultHeader.vue';
</script>

<template>
    <div>
        <DefaultSidebar />
        <div>
            <DefaultHeader />
            <main>
                <slot />
            </main>
        </div>
    </div>
  </template>