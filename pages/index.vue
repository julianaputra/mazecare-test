<script setup lang="ts">
import PatientInformation from '~/components/sections/patient/PatientInformation.vue';
import MedicalRecords from '~/components/sections/patient/MedicalRecords.vue';
import MedicalRecordDetail from '~/components/sections/patient/MedicalRecordDetail.vue';
import MeanBlood from '~/components/sections/patient/MeanBlood.vue';

const isShowResult = ref(false)
const isShowChart = ref(false)

const showResult = () => {
    isShowResult.value = true
}
const showChart = () => {
    isShowChart.value = true
}
</script>

<template>
    <PatientInformation />
    <MedicalRecords @clickResult="showResult" />

    <USlideover v-model="isShowResult" :ui="{ wrapper: 'p-3', background: 'rounded-lg', width: 'max-w-[45%]' }" prevent-close >
        <MedicalRecordDetail @clickChart="showChart" @close="isShowResult = false"  />
    </USlideover>

    <USlideover :overlay="false" side="left" v-model="isShowChart" prevent-close :ui="{ wrapper: 'w-[55%] p-3', background: 'rounded-lg', width: 'max-w-[100%]' }">
        <MeanBlood @close="isShowChart = false" />
    </USlideover>


</template>