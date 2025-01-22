<script setup lang="ts">
import LabResultItem from './LabResultItem.vue';
import UiPagination from '~/components/ui/UiPagination.vue';

const links = [
    {
        label: 'All Records',
        icon: 'ph:heart-duotone',
        to: '/'
    },
    {
        label: 'Allergy/Intolerance',
        icon: 'ph:virus-duotone',
        to: '/allergy'
    },
    {
        label: 'Body Measurements',
        icon: 'ph:person-arms-spread-duotone',
        to: '/body-measurements'
    },
    {
        label: 'Clinical Notes',
        icon: 'ph:clipboard-text-duotone',
        to: '/clinical-notes'
    },
    {
        label: 'Heart',
        icon: 'ph:heart-duotone',
        to: '/heart'
    },
    {
        label: 'Lab Results',
        icon: 'ph:flask-duotone',
        to: '/lab-results'
    },
]

const labResults = [
    {
        id: 1,
        name: 'Diabetes Control Tests',
        value: null,
        unit: 'Recorded'
    },
    {
        id: 2,
        name: 'HbA1c',
        value: 11.5,
        unit: '%'
    },
    {
        id: 3,
        name: 'Mean Blood',
        value: 160,
        unit: 'mg/dL'
    },
    {
        id: 4,
        name: 'Glucose',
        value: 160,
        unit: 'mg/dL'
    },
]

const emit = defineEmits(['clickResult'])

const page = ref(1)
</script>

<template>
    <UCard>
        <template #header>
            <div class="medical-records__header">
                <h4>Records</h4>
                <p>Manage patient medical records</p>
            </div>
        </template>

        <div class="medical-records__body">
            <UVerticalNavigation :links="links" />
            <div class="all-records">
                <div class="all-records__header">
                    <h5>Lab Results</h5>
                    <div class="all-records__actions">
                        <UInput icon="ph:magnifying-glass-duotone" variant="outline" placeholder="Search..." />
                        <UButton icon="ph:plus">Lab Result</UButton>
                    </div>
                </div>

                <LabResultItem @click="() => emit('clickResult')" v-for="result in labResults" :key="result.id"
                    :name="result.name" :value="result.value" :unit="result.unit" />

                <UiPagination v-model="page" :total="labResults.length" />
            </div>
        </div>
    </UCard>


</template>

<style scoped>
.medical-records__header h4 {
    @apply text-base font-semibold;
}

.medical-records__header p {
    @apply text-xs;
}

.medical-records__body {
    display: grid;
    grid-template-columns: 204px 1fr;
    gap: 10px;
}

.all-records__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    @apply mb-3;
}

.all-records__header h5 {
    @apply text-base font-semibold;
}

.all-records__actions {
    display: grid;
    grid-template-columns: 207px auto;
    gap: 8px;
}
</style>