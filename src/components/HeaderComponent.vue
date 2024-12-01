<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
//import { RouterLink } from 'vue-router';

const props = defineProps({
  logo: String,
  toggleSidebar: Function,
  totalQuantity: Number,
  isDark: Function
});

const menu = ref(null);
const navbar = ref(null);


const handleScroll = () => {
  if (menu.value && navbar.value) {
    menu.value.classList.remove('bx-x');
    navbar.value.classList.remove('open');
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <header>
        <span class="logo">
            <img :src="props.logo" alt="Home" id="logo" loading="eager" width="100px" height="auto" aria-label="Home">
        </span>
        <ul ref="navbar" class="navbar">
            <li class="active">
                Home
            </li>
        </ul>
  </header>
</template>