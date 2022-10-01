<template>
  <section class="px-25 pt-12 pb-4">
    <p class="text-10 text-600 text-uppercase mb-6">
      Productos
    </p>
    <section class="d-grid grid-columns-3 lg:grid-template-columns-3 gap-x-5">
      <section
        v-for="(product, index) in products"
        :key="index"
      >
        <section>
          <img
            class="full-dimension object-cover border-radius-4"
            :src="require('@/assets/images/coffee.jpg')"
            alt=""
          >
          <p class="text-8 text-center pt-4 pb-2 px-10">
            {{ product.description }}
          </p>
          <p class="text-7 text-gray-2 text-center">
            Desde S/. {{ product.price }}
          </p>

          <section class="flex-center mt-4 mb-8">
            <button
              type="button"
              class="btn btn-rounded btn-sm btn-primary"
              @click="openModal(index)"
            >
              Ver más
            </button>
          </section>
        </section>
      </section>
    </section>

    <ModalComponent
      v-if="showModal"
      size="md"
      @close-modal="showModal = false"
    >
      <section>
        <p class="text-8 text-uppercase mb-4">
          Detalles del producto
        </p>
        <section>
          {{ currentProduct.description }}
        </section>
      </section>
    </ModalComponent>
  </section>
</template>

<script lang="ts" setup>
import { Ref, ref, computed } from 'vue'
import { Product } from '@/interfaces'
import ModalComponent from '@/components/ModalComponent.vue'

const showModal: Ref<boolean> = ref(false)
const currentIndexProduct: Ref<number> = ref(-1)

const products: Product[] = [
  {
    description: 'CAFÉ ORGÁNICO A GRANEL POR KILO',
    price: '65.00'
  },
  {
    description: 'CAFÉ PREMIUM ORGÁNICO POR 250 GRAMOS',
    price: '25.00'
  },
  {
    description: 'CAFÉ PREMIUM ORGÁNICO POR 500 GRAMOS',
    price: '45.00'
  }
]

const currentProduct = computed(() => products[currentIndexProduct.value])

function openModal (indexProduct: number): void {
  currentIndexProduct.value = indexProduct
  showModal.value = true
}
</script>
