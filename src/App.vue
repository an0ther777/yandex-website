<template>
  <div>
    <input type="text" v-model="textInInput">
    <a :href="searchUrl" target="_blank">
      <button>Поиск</button>
    </a>
  </div>

  <div>
    Текущая ссылка: {{ searchUrl }}
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const textInInput = ref('')

const searchUrl = computed(() => {
  return `https://ya.ru/search/?text=${encodeURIComponent(textInInput.value)}&lr=11143&clid=2270453&win=701&search_source=yaru_desktop_common&search_domain=yaru`
})

function redirectToSearch() {
  if (textInInput.value.trim()) {
    window.location.href = searchUrl.value
  }
}
</script>

<style scoped>

</style>