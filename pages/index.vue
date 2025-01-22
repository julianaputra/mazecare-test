<script setup lang="ts">
import PatientInformation from '~/components/sections/patient/PatientInformation.vue';
import MedicalRecords from '~/components/sections/patient/MedicalRecords.vue';
import MedicalRecordDetail from '~/components/sections/patient/MedicalRecordDetail.vue';
import MeanBloodChart from '~/components/sections/patient/MeanBloodChart.vue';

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

    <USlideover v-model="isShowResult">
        <MedicalRecordDetail @clickChart="showChart" />
    </USlideover>

    <USlideover side="left" v-model="isShowChart">
        <MeanBloodChart />
    </USlideover>
</template>