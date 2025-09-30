<template>
    <div class="main">
        <a :href="link" style="text-decoration: none; color: white;">
            <img style="box-shadow: 2px 2px 3px 3px rgba(255, 255, 255, 0.3); padding: 70px; border: 3px solid white; border-radius: 15px;" 
            :href="link" class="img" :src="imageUrl" :alt="title">
            <h5 class="textInImg">{{ title }}</h5>
        </a>
    </div>
</template>

<script setup lang="ts">
// import { computed } from 'vue'

interface Props {
  imageUrl?: string
  title: string
  link?: string
  imgScale?: number 
}

const props = defineProps<Props>()

// const imgStyle = computed(() => {
//   return {
//     transform: props.imgScale ? `scale(${props.imgScale})` : 'none'
//   }
// })
</script>

<style scoped>

</style>