<script lang="ts" setup>
import MeanBloodChart from './MeanBloodChart.vue';
import MeanBloodList from './MeanBloodList.vue';

import type { IMeanBlood } from '~/types';

const meanBloodList: IMeanBlood[] = [
  { id: 1, value: 18, date: "2024-09-23" },
  { id: 2, value: 22, date: "2024-09-15" },
  { id: 3, value: 30, date: "2024-07-10" },
  { id: 4, value: 25, date: "2024-06-05" },
  { id: 5, value: 20, date: "2024-05-20" },
];

const emit = defineEmits(['close'])
</script>

<template>
    <div class="h-full overflow-auto">
      <div class="py-4 px-5 border-b border-dashed border-gray-300">
        <MeanBloodChart :data="meanBloodList" @close="() => emit('close')" />
      </div>
      <div class="py-4 px-5">
        <MeanBloodList :data="meanBloodList" />
      </div>
    </div>
</template>
