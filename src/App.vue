<script setup>
import { computed , ref } from "vue";
import PWABadge from './components/PWABadge.vue'
import stickyHeader from './components/stickyHeader.vue'
import stickyFooter from './components/stickyFooter.vue'
import insurance from './views/insurance.vue'
import home from './views/homePage.vue'
import income from './views/income.vue'

const activePage = ref(0)

function setPageChange(page){
  activePage.value = page
}

const map = {
  0:home,
  1:insurance,
  2:income
}

const component = computed(() => {
  return map[activePage.value]
})
</script>
<template>
  <stickyHeader/>
  <KeepAlive>
    <component :is="component"/>
  </KeepAlive>
  <stickyFooter @pageChange="setPageChange"/>
  <PWABadge />
</template>
<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
