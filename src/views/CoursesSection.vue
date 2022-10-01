<template>
  <section class="px-25 py-10 lg:px-10">
    <p class="text-14 text-600 mb-6 text-italic text-center">
      ¿Te gustaría aprender sobre el mundo de las criptomonedas?
    </p>
    <section class="flex-center">
      <section class="h-26 w-50 lg:w-90 lg:h-20">
        <img
          :src="require('@/assets/images/criptomonedas.jpg')"
          class="full-dimension object-cover border-radius-4 shadow-4"
          alt=""
        >
      </section>
    </section>

    <p class="text-12 text-primary text-600 mt-12 text-italic text-center pb-4">
      Te invito a revisar los siguientes enlaces de videos!
    </p>

    <section
      v-for="(courseLink, index) in courseLinks"
      :key="index"
      class="flex-center"
    >
      <p
        class="text-10 cursor-pointer py-1 hover:text-blue"
        @click="openLink(courseLink.link)"
      >
        {{ courseLink.description }}
      </p>
    </section>
  </section>
</template>

<script lang="ts" setup>
import { CourseLink } from '@/interfaces'

const courseLinks: CourseLink[] = [
  {
    description: 'Esta es la primera descripción de un enlace a un video',
    link: 'https://www.youtube.com/watch?v=CXmXi9tLPfU'
  },
  {
    description: 'Esta es la segunda descripción de un enlace a un video',
    link: 'https://www.youtube.com/watch?v=CXmXi9tLPfU'
  },
  {
    description: 'Esta es la tercera descripción de un enlace a un video',
    link: 'https://www.youtube.com/watch?v=CXmXi9tLPfU'
  },
  {
    description: 'Esta es la cuarta descripción de un enlace a un video',
    link: 'https://www.youtube.com/watch?v=CXmXi9tLPfU'
  },
  {
    description: 'Esta es la quinta descripción de un enlace a un video',
    link: 'https://www.youtube.com/watch?v=CXmXi9tLPfU'
  },
  {
    description: 'Esta es la sexta descripción de un enlace a un video',
    link: 'https://www.youtube.com/watch?v=CXmXi9tLPfU'
  }
]

function openLink (url: string): void {
  window.open(url, '_blank')
}

</script>
