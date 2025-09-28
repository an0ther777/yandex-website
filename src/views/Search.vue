<template>
  <div class="cover">
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
  width: clamp(300px, 80vw, 960px);
  margin: 0 auto;
  border-radius: 20px;
  background-color: rgb(48, 48, 48);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 15px;
  gap: 20px;
  position: relative;
}

.searchInput {
  padding: 15px 300px 15px 15px;
  flex: 1;
  font-size: 16px;
  border: none;
  border-radius: 20px;
  min-width: 200px;
  transition: transform 1s ease, background-color 0.6s ease;
  background-color: rgb(59, 59, 59);
  color: rgb(219, 219, 219);
  text-align: left;
}
.searchInput:focus {
    transform: translateX(-10vh);
    background-color: rgb(61, 61, 61);
    outline: none;
}


</style>