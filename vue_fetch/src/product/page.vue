<script setup>
//後端提供的資料串接網址https://cwpeng.github.io/live-records-samples/data/products.json
import { onMounted, ref } from 'vue'
import List from "./list.vue";
let products = ref(null) //建立響應式狀態 products ，一開始是空值 null

//組件掛載完成後，開始呼叫fetch串接後端的資料
onMounted(async () => {
  const response = await fetch('https://cwpeng.github.io/live-records-samples/data/products.json')
  let data = await response.json()
  products.value = data
})
</script>

<template>
  <div v-if="products === null">資料載入中</div>
  <List v-else :products="products"  ></List>

</template>

<style scoped>


</style>
