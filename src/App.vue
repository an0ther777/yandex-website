<template>
  <h6 id="mainImg"></h6>
  <a href="#mainImg">
    <img src="../public/icon/Yandex-Logo-PNG-HD-Images.png" class="mainImg">
  </a>
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
.mainImg{
  position: fixed;
  height: 30px;
  margin: 5px 30px;
  cursor: pointer;
  border-radius: 14px;
  box-shadow: 1px 0px 3px 3px rgba(255, 255, 255, 0.05);
  transition: all 1s;
}
.mainImg:hover{
  transform: scale(1.2)
}

</style>