<template>
  <main>
    <HomeComponent />
    <Suspense>
      <template #default>
        <CategoriesComponent/>
      </template>
      <template #fallback>
        <Loading />
      </template>
    </Suspense>
    <Suspense>
      <template #default>
        <History/>
      </template>
      <template #fallback>
        <Loading />
      </template>
    </Suspense>
    <Suspense>
      <template #default>
        <Services/>
      </template>
      <template #fallback>
        <Loading />
      </template>
    </Suspense>
    <Suspense>
      <template #default>
        <Newsletter/>
      </template>
      <template #fallback>
        <Loading />
      </template>
    </Suspense>
    <a href="#" class="scrolltop" id="scroll-top">
      <i class='bx bxs-up-arrow scrolltop-icon'></i>
    </a>
    <Suspense>
      <template #default>
        <ContactFooter :logo="logo"/>
      </template>
      <template #fallback>
        <Loading />
      </template>
    </Suspense>
  </main>
</template>

<script>
import { defineAsyncComponent } from 'vue';
import HomeComponent from '@/components/HomeComponent.vue';
import Loading from '@/loaders/Loading.vue';

const CategoriesComponent = defineAsyncComponent(() =>
  new Promise(resolve => {
    setTimeout(() => {
      resolve(import('@/components/CategoriesComponent.vue'));
    }, 1000)
  })
);
const History = defineAsyncComponent(() =>
  new Promise(resolve => {
    setTimeout(() => {
      resolve(import('@/components/History.vue'));
    }, 1500)
  })
);
const Services = defineAsyncComponent(() =>
  new Promise(resolve => {
    setTimeout(() => {
      resolve(import('@/components/Services.vue'));
    }, 1500)
  })
);
const Newsletter = defineAsyncComponent(() =>
  new Promise(resolve => {
    setTimeout(() => {
      resolve(import('@/components/Newsletter.vue'));
    }, 2200)
  })
);
const ContactFooter = defineAsyncComponent(() =>
  new Promise(resolve => {
    setTimeout(() => {
      resolve(import('@/components/ContactFooter.vue'));
    }, 3100)
  })
);

export default {
  name: 'HomeView',
  props: ['logo'],
  components: {
    HomeComponent,
    CategoriesComponent,
    History,
    Services,
    Newsletter,
    ContactFooter,
    Loading
  }
}
</script>
