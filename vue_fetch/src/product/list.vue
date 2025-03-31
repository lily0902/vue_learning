<script setup>
defineProps(["products"]);
</script>
<template>
  <div class="list">
    <div class="products" v-for:="product in products">
      <div class="name">{{ product.name }}</div>
      <div class="description">單價: {{ product.price }}</div>
      <div class="price">{{ product.description }}</div>
    </div>
  </div>
</template>
<style scoped>
.list{
  line-height:1.5rem;
}
.products{
  padding:15px 0px;
  border-bottom:1px solid #dddddd;
}
.products>.name{
  font-weight:bold;
}
</style>
