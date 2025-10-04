<template>
  <h6 id="mainImg"></h6>
  <a href="#mainImg">
    <img src="../public/icon/Yandex-Logo-PNG-HD-Images.png" class="mainImg">
  </a>
  
<div class="main">
  <div style="margin-top: 15%;" class="mainImgMany">
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
      <ButtonImg :img-scale="1.6" link="https://yandex.ru/medicine?utm_source=subclasses_product&utm_content=med_doc&utm_campaign=home_web&pers_suggest=0"
        imageUrl="../public/icon/vecteezy_medical-red-first-aid-kit-with-medicine-on-transparent_54044054.png" 
        title="Медицина"
      />
  </div>

  <div class="search">
    <Search/>
  </div>

  <div>
    <CourseWeather/>
  </div>

  <div class="ads-container">
    <div class="ads-flex">
      <BlocksBottomSearch title="Реклама 1"/>
      <BlocksBottomSearch title="Реклама 2"/>
      <BlocksBottomSearch title="Реклама 3"/>
      <BlocksBottomSearch title="Реклама 4"/>
      <BlocksBottomSearch title="Реклама 5"/>
      <BlocksBottomSearch title="Реклама 6"/>
    </div>
  </div>
</div>
</template>

<script setup lang="ts">
import CourseWeather from './views/CourseWeather.vue';
import BlocksBottomSearch from './views/BlocksBottomSearch.vue';
import ButtonImg from './UI/ButtonImg.vue';
import Search from './views/Search.vue';
</script>

<style scoped>
.main{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  box-sizing: border-box;
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
.ads-container {
  width: 100%;
  padding: 20px;
  box-sizing: border-box;
}

.ads-flex {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 1200px;
  margin: 0 auto;
}

.ads-flex > * {
  flex: 1 1 calc(33.333% - 20px);
  min-width: 200px;
  max-width: 300px;
}

/* Адаптивность */
@media (max-width: 768px) {
  .ads-flex > * {
    flex: 1 1 calc(50% - 20px);
  }
}

@media (max-width: 480px) {
  .ads-flex > * {
    flex: 1 1 100%;
  }
}
</style>