<script setup lang="ts">
const items = [
    [{
        label: 'ben@example.com',
        slot: 'account',
        disabled: true
    }], [{
        label: 'Settings',
        icon: 'i-heroicons-cog-8-tooth'
    }], [{
        label: 'Documentation',
        icon: 'i-heroicons-book-open'
    }, {
        label: 'Changelog',
        icon: 'i-heroicons-megaphone'
    }, {
        label: 'Status',
        icon: 'i-heroicons-signal'
    }], [{
        label: 'Sign out',
        icon: 'i-heroicons-arrow-left-on-rectangle'
    }]
]

const locales = ['en-US', 'id-ID']

const country = ref(locales[0])
</script>

<template>
    <header class="border-b border-gray-200 bg-gray-50 px-6 flex items-center justify-end h-[62px] sticky top-0 z-[49]">
        <div class="flex items-center gap-8">
            <button class="flex">
                <UIcon name="ph:magnifying-glass-duotone" class="w-6 h-6" />
            </button>
            <button class="flex">
                <UIcon name="ph:sun-duotone" class="w-6 h-6" />
            </button>

            <USelect v-model="country" :options="locales" />

            <UDropdown :items="items" :ui="{ item: { disabled: 'cursor-text select-text' } }"
                :popper="{ placement: 'bottom-start' }">
                <UAvatar size="sm" src="https://avatars.githubusercontent.com/u/739984?v=4" />

                <template #account="{ item }">
                    <div class="text-left">
                        <p>
                            Signed in as
                        </p>
                        <p class="truncate font-medium text-gray-900 dark:text-white">
                            {{ item.label }}
                        </p>
                    </div>
                </template>

                <template #item="{ item }">
                    <span class="truncate">{{ item.label }}</span>

                    <UIcon :name="item.icon" class="flex-shrink-0 h-4 w-4 text-gray-400 dark:text-gray-500 ms-auto" />
                </template>
            </UDropdown>
        </div>
    </header>
</template>