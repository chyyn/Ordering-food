<script setup>
  import { RouterView } from 'vue-router'
</script>
<template>
  <HeaderComponent :isDark="isDark" :logo="bannerlogo" />
  <RouterView :logo="bannerlogo" :inventory="isProductsPage ? inventory : null" :addToCart="isProductsPage ? addToCart : null"/>
  <transition name="cart-transition" mode="out-in">
  <Sidebar
      v-if="showSidebar"
      :toggle="toggleSidebar"
      :cart="cart"
      :inventory="inventory"
      :remove="removeItem"
   />
  </transition>
</template>

<script>
  import { defineAsyncComponent } from 'vue'
  import { initializeScrollTop } from '@/lib/script'
  import logo from '@/assets/images/logo.webp'
  //import whitelogo from '@/assets/images/logo-white.webp'
  import HeaderSketelon from '@/loaders/HeaderSketelon.vue'
  const HeaderComponent = defineAsyncComponent({
    loader: () => import('@/components/HeaderComponent.vue'),
    loadingComponent: HeaderSketelon,
    suspensible: false
  })

  export default {
    components: {
      HeaderComponent,
    },
    data() {
      return {
        bannerlogo: logo,
        cart: {}
      }
    },
    computed: {
      totalQuantity() {
        return Object.values(this.cart).reduce((acc, curr) => { return acc + curr }, 0)  
      },
      isProductsPage() {
        return this.$route.name == 'ProductsView';
      }
    },
    methods: {
    },
    mounted() {
        initializeScrollTop()
    }
  }
</script>


<style scoped>
.cart-transition-enter-active, .cart-transition-leave-active {
  opacity: 1;
  transform: translateY(0);
}

.cart-transition-enter, .cart-transition-leave-to {
  opacity: 0;
  transform: translateY(-20px);
  transition: opacity 0.5s, transform 0.5s ease-in-out;
}
</style>