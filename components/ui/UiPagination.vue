<script setup lang="ts">
interface IProps {
    total: number
}

const props = defineProps<IProps>()

const itemsPerPageOptions = [
    {
        name: 'Show 5',
        value: 5
    },
    {
        name: 'Show 10',
        value: 10
    },
    {
        name: 'Show 20',
        value: 20
    },
]

const itemsPerPage = ref(10)

const page = defineModel<number>({ required: true })

const startItem = computed(() => (page.value - 1) * itemsPerPage.value + 1);
const endItem = computed(() => Math.min(page.value * itemsPerPage.value, props.total));

</script>

<template>
    <div class="ui-footer">
        <div class="ui-footer__info">
            <p>Showing {{ startItem }} to {{ endItem }} of {{ total }} entries</p>
            <USelect v-model="itemsPerPage" :options="itemsPerPageOptions" option-attribute="name" size="xs" />
        </div>
        <UPagination v-model="page" :page-count="itemsPerPage" :total="total" />
    </div>
</template>

<style scoped>
.ui-footer {
    @apply flex items-center justify-between;
}

.ui-footer__info {
    @apply text-xs flex items-center gap-2;
}
</style>