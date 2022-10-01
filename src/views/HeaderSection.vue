<template>
  <header class="fixed w-100 z-50 top-0 left-0 lg:relative">
    <nav class="d-flex justify-space-between bg-secondary h-7 px-25 lg:px-0">
      <section class="d-flex items-center text-white text-11">
        <section class="h-6">
          <img
            class="full-dimension object-cover"
            :src="require('@/assets/images/logo.jpg')"
            alt=""
          >
        </section>
        <span
          class="cursor-pointer text-uppercase text-black"
          @click="clickLink('homeRef')"
        >Bitcoffee</span>
      </section>

      <ul class="d-flex items-center lg:d-none">
        <li
          v-for="(link, index) in reactiveLinks"
          :key="index"
          class="px-9"
        >
          <a
            class="cursor-pointer text-8 text-black"
            @click="clickLink(link.refName)"
          >{{ link.text }}</a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts" setup>
import { withDefaults, defineProps, defineEmits, reactive } from 'vue'
import { Link } from '@/interfaces'

interface Props {
  links: Link[]
}

const props = withDefaults(defineProps<Props>(), {
  links: () => []
})

const emit = defineEmits<{
  (e: 'click-link', refName: string): void
}>()

const reactiveLinks = reactive(props.links)

function clickLink (refName: string): void {
  emit('click-link', refName)
}
</script>
