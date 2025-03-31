<script setup>
//產品資料串接網址 https://cwpeng.github.io/live-records-samples/data/products.json
//評論資料串接網址 https://cwpeng.github.io/live-records-samples/data/reviews.json
//建立一個標籤選單做內容切換
import Page from './product/page.vue';
import Review from './review/review.vue';
import { ref } from 'vue';
//紀錄一個page的響應式狀態，用來決定現在要看的是哪一個內容 product 還是 review， 預設為 product
let page = ref("product");
let change = function (clickedPage) {
  page.value = clickedPage;
}

</script>
<template>
  <nav>
    <span :class="page==='product'?'current':''" @click="change('product')">產品資料</span>
    <span :class="page==='review'?'current':''" @click="change('review')">評論訊息</span>
  </nav>
  <Page v-if="page==='product'"></Page>
  <Review v-if="page==='review'"></Review>

</template>
<style scoped>
  nav{font-size:20px;}
  nav>span{margin-right:10px;}
  nav>span.current{font-weight:bold}
</style>
