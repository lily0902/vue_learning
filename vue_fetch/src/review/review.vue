<script setup>
import { onMounted, ref } from 'vue'
import reviewList from './reviewList.vue';
let reviews = ref(null) //建立響應式狀態 review ，一開始是空值 null

//組件掛載完成後，開始呼叫fetch串接後端的資料
onMounted(async () => {
  const response = await fetch('https://cwpeng.github.io/live-records-samples/data/reviews.json')
  let review = await response.json()
  reviews.value = review

})
</script>
<template>
  <div v-if="reviews===null">資料載入中</div>
  <reviewList v-else :reviews="reviews"></reviewList>

</template>
<style scoped></style>
  