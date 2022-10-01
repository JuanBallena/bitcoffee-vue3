<template>
  <main>
    <section ref="homeRef">
      <HeaderSection
        :links="links"
        @click-link="goToSection($event)"
      />
    </section>

    <MainImageSection />

    <section ref="productsRef">
      <ProductsSection />
    </section>

    <section ref="investmentsRef">
      <InvestmentsSection />
    </section>

    <section ref="coursesRef">
      <CoursesSection />
    </section>

    <section ref="marketRef">
      <MarketSection />
    </section>

    <FooterSection />
  </main>
</template>

<script lang="ts" setup>
import { onMounted, ref, Ref } from 'vue'
import HeaderSection from './HeaderSection.vue'
import MainImageSection from './MainImageSection.vue'
import ProductsSection from './ProductsSection.vue'
import InvestmentsSection from './InvestmentsSection.vue'
import CoursesSection from './CoursesSection.vue'
import MarketSection from './MarketSection.vue'
import FooterSection from './FooterSection.vue'
import { Link } from '@/interfaces'

const homeLink = {
  text: '',
  refName: 'homeRef'
}

const productsLink = {
  text: 'Productos',
  refName: 'productsRef'
}

const investmentsLink = {
  text: 'Inversiones',
  refName: 'investmentsRef'
}

const coursesLink = {
  text: 'Cursos',
  refName: 'coursesRef'
}

const marketLink = {
  text: 'Mercado',
  refName: 'marketRef'
}

const links: Ref<Link[]> = ref([])
links.value.push(productsLink)
links.value.push(investmentsLink)
links.value.push(coursesLink)
links.value.push(marketLink)

const homeRef = ref(null)
const productsRef = ref(null)
const investmentsRef = ref(null)
const coursesRef = ref(null)
const marketRef = ref(null)
const headerHeight = ref(0)

onMounted(() => {
  if (homeRef.value != null) {
    const homeRefHtml = homeRef.value as HTMLElement
    const header = homeRefHtml.children[0].children[0] as HTMLElement
    headerHeight.value = header.offsetHeight
  }
})

function goToSection (refName: string): void {
  let ref = null

  if (refName === homeLink.refName) {
    ref = homeRef.value
  }

  if (refName === productsLink.refName) {
    ref = productsRef.value
  }

  if (refName === investmentsLink.refName) {
    ref = investmentsRef.value
  }

  if (refName === coursesLink.refName) {
    ref = coursesRef.value
  }

  if (refName === marketLink.refName) {
    ref = marketRef.value
  }

  if (ref != null) {
    const refHtml = ref as HTMLElement
    const top = refHtml.offsetTop - headerHeight.value
    window.scrollTo(0, top)
  }
}
</script>
