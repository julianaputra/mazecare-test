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
  <div class="info">
    <div class="info__header">
      <div class="info__header-avatar">
        <UAvatar size="lg" src="https://avatars.githubusercontent.com/u/739984?v=4" alt="Avatar" />
        <div>  
          <h2>Abhishek</h2>
          <p>P00004</p>
        </div>
      </div>
      <div class="info__header-action">
        <UButton icon="ph:trash-duotone" size="sm" color="white" square variant="solid" />
      </div>
    </div>
    <div class="info__tabs">
      <UHorizontalNavigation :links="links" class="border-b border-gray-200 dark:border-gray-800" />
    </div>
  </div>
</template>

<style scoped>
.info {
  @apply border border-gray-200 rounded-md mb-3 grid bg-white;
}

.info__header {
  @apply border-b border-gray-200 grid;
  grid-template-columns: auto 1fr;
}

.info__header-avatar {
  @apply px-6 py-4 border-e border-gray-200 flex items-center;
  gap: 12px;
}

.info__header-avatar h2 {
  @apply font-semibold;
}
.info__header-avatar p {
  @apply text-sm text-gray-400;
}

.info__header-action {
  @apply px-6 py-4 text-end;
}


.info__tabs {
  @apply px-4;
}
</style>