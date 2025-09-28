<template>
  <h6 id="mainImg"></h6>
  <a href="#mainImg">
    <img src="../public/icon/Yandex-Logo-PNG-HD-Images.png" class="mainImg">
  </a>
<div class="main">
  <div class="mainImgMany">
    <ButtonImg link="https://yandex.ru/finance?utm_source=subclasses_product&utm_content=fin_5&utm_campaign=home_web&pers_suggest=0"
        imageUrl="../public/icon/vecteezy_leadership-for-successful-new-idea-excellent-business-graph_9315255.png" 
        title="Финансы"
      />
      <ButtonImg :img-scale="1.4" link="https://yandex.ru/realty/?utm_source=subclasses_realty&utm_content=realty&utm_campaign=home_web"
        imageUrl="../public/icon/vecteezy_3d-interior-design_10880101.png" 
        title="Квартиры"
      />
      <ButtonImg :img-scale="1.22" link="https://yandex.ru/products?utm_source=subclasses_product&utm_content=ecom&utm_campaign=home_web&pers_suggest=0"
        imageUrl="../public/icon/vecteezy_3d-check-product_28047017.png" 
        title="Товары"
      />
      <ButtonImg link="https://yandex.ru/medicine?utm_source=subclasses_product&utm_content=med_doc&utm_campaign=home_web&pers_suggest=0"
        imageUrl="../public/iпcon/vecteezy_medical-red-first-aid-kit-with-medicine-on-transparent_54044054.png" 
        title="Медицина"
      />
  </div>
  <div class="search">
    <Search/>
  </div>
</div>
</template>

<script setup lang="ts">
import ButtonImg from './UI/ButtonImg.vue';
import Search from './views/Search.vue';
</script>

<style scoped>
.main{
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
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
.mainImgMany{
  display: flex;
  align-items: center;
}
</style>