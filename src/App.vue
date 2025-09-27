<template>
<div class="main">
  <div class="search">
    <Search/>
  </div>
</div>
</template>

<script setup lang="ts">
import Search from './views/Search.vue';
</script>

<style scoped>
.main{
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>