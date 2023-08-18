<script setup>
import NewsPageComp from "./pages/NewsList.vue";

import HeaderComp from "./components/HeaderComp.vue";
import FooterComp from "./components/FooterComp.vue";
</script>

<template>
  <div>
    <header-comp></header-comp>
    <NewsPageComp/>
    <footer-comp></footer-comp>
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
}
</style>
