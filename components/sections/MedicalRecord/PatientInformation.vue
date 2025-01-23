<script setup lang="ts">
const links = [
  {
    label: 'Patient Details',
    to: '/patient-details'
  },
  {
    label: 'Appointments',
    to: '/appointments'
  },
  {
    label: 'Records',
    to: '/'
  }
]
</script>

<template>
  <div class="border border-gray-200 rounded-md mb-3 grid bg-white">
    <div class="border-b border-gray-200 flex justify-between">
      <div class="px-6 py-4 border-e border-gray-200 flex items-center gap-3">
        <UAvatar size="lg" src="https://avatars.githubusercontent.com/u/739984?v=4" alt="Avatar" />
        <div>
          <h2 class="font-semibold">Abhishek</h2>
          <p class="text-sm text-gray-400">P00004</p>
        </div>
      </div>
      <div class="px-6 py-4 text-end">
        <UButton icon="ph:trash-duotone" size="sm" color="white" square variant="solid" />
      </div>
    </div>
    <div class="px-4">
      <UHorizontalNavigation :links="links" class="border-b border-gray-200 dark:border-gray-800" />
    </div>
  </div>
</template>