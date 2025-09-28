<template>
    <div style="margin: 0 10px 30px 0;">
        <a :href="link" style="text-decoration: none; color: white;">
        <img :style="imgStyle" :href="link" class="img" :src="imageUrl" :alt="title">
         <h5 class="textInImg">{{ title }}</h5>
        </a>
    </div>
</template>

<script lang="ts" setup>
import { computed } from 'vue'

interface Props {
  imageUrl: string
  title: string
  link: string
  imgScale?: number 
}

const props = defineProps<Props>()

const imgStyle = computed(() => {
  return {
    transform: props.imgScale ? `scale(${props.imgScale})` : 'none'
  }
})
</script>

<style scoped>
.img{
  height: 30px;
  margin: 5px 30px;
  cursor: pointer;
  transition: all 1s;
} 
.textInImg{
    margin: 0px 0px 10px 20px;
    font-weight: lighter;
}
</style>