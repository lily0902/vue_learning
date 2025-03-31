<script setup>
    import { ref, onMounted,onUnmounted } from 'vue'
    
    let text2 = ref('這是預設的內容文字')
    defineProps(["title", "subtitle"]);
    let changeText = function () {
        text2.value = '這是新的內容文字'
}
//製作一個 Counter 數數的功能
let counter = ref(0);
let scheduledId;

//組件掛載時，設定每秒加一的排程
onMounted(function () {
    scheduledId = window.setInterval(function () {
        console.log("每隔一秒鐘，數字加1");
        counter.value += 1;
    }, 1000);
});

//組件卸載的時候，清除掛載時設定的排程
onUnmounted(function () {
    console.log("scheduledId:", scheduledId);
    window.clearInterval(scheduledId);
});

</script>
<template>
    <nav>
        <div>{{ counter }}</div>
        <div>{{ title }}</div>
        <div>{{ subtitle }}</div>
    </nav>
    <div>{{ text2 }}</div>
    <button @click="changeText">改變內容文字</button>

</template>
<style scoped>
    nav{
        padding:10px;
    }
</style>