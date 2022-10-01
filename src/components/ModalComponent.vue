<template>
  <Teleport to="body">
    <section class="fixed left-0 top-0 h-100vh w-100 flex-center z-90 bg-dark-800">
      <section
        :class="getSize()"
        class="relative overflow-y-auto max-h-90vh border-radius-3 py-7 px-8 mx-4 shadow-1 bg-white scrollbar-default"
      >
        <div
          class="absolute top-15px right-4 text-gray-2 cursor-pointer text-8"
          @click="$emit('close-modal')"
        >
          x
        </div>
        <slot />
      </section>
    </section>
  </Teleport>
</template>

<script lang="ts" setup>
import { defineEmits, withDefaults, defineProps } from 'vue'

interface Props {
  size: string
}

const props = withDefaults(defineProps<Props>(), {
  size: ''
})

defineEmits<{
  (e: 'close-modal'): void
}>()

function getSize (): string {
  if (props.size === 'sm') {
    return 'w-30'
  }

  if (props.size === 'md') {
    return 'w-50'
  }

  return 'w-100'
}
</script>
