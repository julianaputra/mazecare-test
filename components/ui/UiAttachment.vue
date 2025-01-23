<script lang="ts" setup>
import type { IAttachment } from '~/types';

interface IProps {
    data: IAttachment
}

const props = defineProps<IProps>()

const iconName = computed(() => {
    if (props.data.type === 'image') {
        return 'ph:image-duotone'
    } else if (props.data.type === 'doc') {
        return 'ph:file-doc-duotone'
    }
})
</script>

<template>
    <div class="border border-gray-300 rounded-md p-2 flex justify-between items-center">
        <div class="flex items-center gap-2">
            <UIcon class="w-5 h-5" :name="iconName" />
            <div>
                <h5 class="text-sm font-semibold mb-1">{{ data.name }}</h5>
                <p class="text-xs text-gray-400">Uploaded at: {{ data.uploaded_at }}</p>
            </div>
        </div>

        <UButton icon="ph:dots-three-outline" size="sm" color="gray" square />
    </div>
</template>