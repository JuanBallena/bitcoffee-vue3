<template>
  <section class="bg-dark px-25 pt-16 pb-8">
    <p class="text-14 text-600 mb-6 text-white pb-6">
      Tendencias del café y el mercado
    </p>

    <section class="d-grid grid-columns-3 gap-x-4">
      <section
        v-for="(i, index) in 6"
        :key="index"
        class="mb-8"
      >
        <section>
          <img
            class="full-dimension object-cover border-radius-4 shadow-5"
            :src="require('@/assets/images/tendencias-coffee.png')"
            alt=""
          >
          <section class="flex-center">
            <p class="text-white py-2 text-8 text-center text-italic line-height-4">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt veritatis molestiae porro illo mollitia fugit optio quas tempora nisi ex autem, provident perspiciatis nostrum voluptas nam? Quasi officiis quos doloremque?
            </p>
          </section>
        </section>
      </section>
    </section>
  </section>
</template>
