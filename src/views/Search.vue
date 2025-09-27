<template>
  <div class="cover">
    <!-- <img src="../../public/icon/Yandex-Logo-PNG-HD-Images.png" 
        style="width: 40px; position: static;"> -->
    <div class="shell">
        <input type="text" v-model="textInInput" 
            class="searchInput" placeholder="Найдется всё" 
            @keyup.enter="handleSearch">
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const textInInput = ref('')

const searchUrl = computed(() => {
  return `https://ya.ru/search/?text=${encodeURIComponent(textInInput.value)}&lr=11143&clid=2270453&win=701&search_source=yaru_desktop_common&search_domain=yaru`
})

function handleSearch() {
  if (textInInput.value.trim()) {
    window.open(searchUrl.value, '_blank')
  }
}
</script>

<style scoped>
.cover {
  width: clamp(300px, 90vw, 960px);
  margin: 0 auto;
  border: 3px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  gap: 20px;
  position: relative;
}

.searchInput {
  padding: 15px 120px;
  flex: 1;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  min-width: 200px;
  transition: transform 1s ease; 
}
.searchInput:focus {
    transform: translateX(-220px);
    border: 0px solid gray;
    background-color: rgb(204, 204, 204);
}


</style>