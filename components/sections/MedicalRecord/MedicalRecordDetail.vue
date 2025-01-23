<script setup lang="ts">
import UiAttachment from '~/components/ui/UiAttachment.vue';
import type { IAttachment } from '~/types';

const emit = defineEmits(['clickChart', 'close'])

const attachmentList: Ref<IAttachment[]> = ref([
  {
    id: 1,
    name: 'BP-Systolic-2024/09/09.jpg',
    uploaded_at: '2024/09/09 12:32 PM',
    type: 'image'
  },
  {
    id: 2,
    name: 'BP-Systolic-2024/09/09.pdf',
    uploaded_at: '2024/09/09 12:32 PM',
    type: 'doc'
  }
])

const generalInformation = ref({
  name: 'BP Systolic',
  description: 'This is description for BP Systolic record',
  summary: 'You are doing great'
})

const questionnaireAnswer = ref({
  answer: 80,
  unit: 'mmHG'
})

const cardUiConfig = {
  body: {
    padding: 'px-4 py-3 sm:p-4'
  },
  header: {
    padding: 'px-4 py-3 sm:px-4'
  },
}

const formGroupUiConfig = {
  label: {
    base: 'block text-xs font-normal text-gray-700 dark:text-gray-200',
  },
}
</script>

<template>
  <div class="h-full overflow-auto">
    <div class="py-3 px-4 border-b border-gray-200 flex justify-between items-center">
      <div>
        <h4 class="text-sm font-semibold">Medical Record Details</h4>
        <p class="text-xs">View and manage medical record details</p>
      </div>
      <UButton icon="ph:x" size="sm" color="gray" square @click.prevent="emit('close')" />
    </div>

    <div class="py-3 px-4 ">
      <div class="rounded-md border border-gray-200 grid grid-cols-4 mb-3">
        <div class="px-4 py-3 border-e">
          <h5 class="text-sm font-semibold">Mean Blood</h5>
          <p class="text-xs text-gray-400 text-ellipsis">This is description for BP ...</p>
        </div>
        <div class="px-4 py-3 border-e">
          <h5 class="text-sm font-semibold">Recorded at</h5>
          <p class="text-xs text-gray-400 text-ellipsis">2024/09/02 02:15:47 PM</p>
        </div>
        <div class="px-4 py-3 col-span-2 text-end">
          <UButton icon="ph:trash-duotone" size="sm" color="white" square variant="solid" />
        </div>
      </div>

      <div class="mb-3 grid grid-cols-3 gap-3">
        <div role="button" @click="() => emit('clickChart')"
          class="border-teal-500 border-2 rounded-md p-2 flex items-start gap-2">
          <div class="rounded-sm p-1 bg-teal-500 text-white">
            <UIcon name="ph:chart-line-up" class="w-4 h-4 block" />
          </div>
          <div>
            <p class="text-xs text-gray-500">See Chart</p>
            <p class="text-sm font-semibold">Mean Blood</p>
          </div>
        </div>
        <div class="border border-gray-200 rounded-md p-2 flex items-start gap-2">
          <div class="rounded-sm p-1 bg-gray-100">
            <UIcon name="ph:user" class="w-4 h-4 block" />
          </div>
          <div>
            <p class="text-xs text-gray-500">Patient</p>
            <p class="text-sm font-semibold">Abhishek</p>
          </div>
        </div>
        <div class="border border-gray-200 rounded-md p-2 flex items-start gap-2">
          <div class="rounded-sm p-1 bg-gray-100">
            <UIcon name="ph:stethoscope" class="w-4 h-4 block" />
          </div>
          <div>
            <p class="text-xs text-gray-500">Provider</p>
            <p class="text-sm font-semibold">Mean Blood</p>
          </div>
        </div>
      </div>

      <UCard class="mb-3" :ui="cardUiConfig">
        <template #header>
          <h4 class="text-sm font-semibold">General Information</h4>
          <p class="text-xs text-gray-400">Information about the record</p>
        </template>
        <div class="space-y-2">
          <UFormGroup :ui="formGroupUiConfig" label="Name" required>
            <UInput v-model="generalInformation.name" />
          </UFormGroup>
          <UFormGroup :ui="formGroupUiConfig" label="Description" required>
            <UInput v-model="generalInformation.description" />
          </UFormGroup>
          <UFormGroup :ui="formGroupUiConfig" label="Summary">
            <UTextarea v-model="generalInformation.summary" />
          </UFormGroup>
        </div>
      </UCard>

      <UCard class="mb-3" :ui="cardUiConfig">
        <template #header>
          <h4 class="text-sm font-semibold">Questionnaire Answer</h4>
          <p class="text-xs text-gray-400">View and manage questionnaire answer</p>
        </template>
        <div class="grid grid-cols-2 gap-2">
          <UFormGroup :ui="formGroupUiConfig" label="Answer" required>
            <UInput v-model="questionnaireAnswer.answer" type="number" />
          </UFormGroup>
          <UFormGroup :ui="formGroupUiConfig" label="Unit" required>
            <UInput v-model="questionnaireAnswer.unit" />
          </UFormGroup>
        </div>
      </UCard>

      <UCard class="mb-3" :ui="cardUiConfig">
        <template #header>
          <div class="flex justify-between items-center">
            <div>
              <h4 class="text-sm font-semibold">Attachments</h4>
              <p class="text-xs text-gray-400">View and manage record attachment</p>
            </div>
            <UButton icon="ph:plus">Upload File</UButton>
          </div>
        </template>
        <div class="grid gap-2">
          <UiAttachment v-for="attachment in attachmentList" :key="attachment.id" :data="attachment" />
        </div>
      </UCard>
    </div>
  </div>
</template>