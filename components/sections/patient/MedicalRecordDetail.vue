<script setup lang="ts">
const emit = defineEmits(['clickChart'])
</script>

<template>
    <div>
        <h4>Medical Record Details</h4>

        <div class="p-4 flex-1">
        <UButton
          color="gray"
          variant="ghost"
          size="sm"
          icon="i-heroicons-x-mark-20-solid"
          class="flex sm:hidden absolute end-5 top-5 z-10"
          square
          padded
          @click="() => emit('clickChart')"
        />

        <UButton  @click="() => emit('clickChart')">
            Chart
        </UButton>
      </div>
    </div>
</template>