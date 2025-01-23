<script setup lang="ts">
import type { IMeanBlood } from '~/types';
import MeanBloodListItem from '~/components/sections/MeanBlood/MeanBloodListItem.vue';
import UiPagination from '~/components/ui/UiPagination.vue';

interface IProps {
    data: IMeanBlood[]
}

defineProps<IProps>()

const page = ref(1)
</script>

<template>
    <div>
        <MeanBloodListItem v-for="item in data" :key="item.id" :value="item.value" :date="item.date" />
        <UiPagination v-model="page" :total="data.length" />
    </div>
</template>