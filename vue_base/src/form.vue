<script setup>
  import { ref } from 'vue'
  let text = ref('預設的文字')
  let color2 = ref(null)
  let fruits = ref([])
  let gender2 = ref('')
  let clearText = function () {
    text.value = ''
}
  let mainText = ref("主要的網站內容");
  let change = function () {
  mainText.value = "網站內容已經改變了";
}
defineProps(["color", "bgr"]);

let emit = defineEmits(["update"]);
let updateParentSubtitle = function () {
  emit("update");
};
</script>
<template>
  <button @click="$emit('update')">改變副標題</button>
  <button @click="updateParentSubtitle">改變副標題2</button>
  <div :style="{
    'background-color': bgr ,
    'color': color
  }">
    <div @click="change">{{ mainText }}</div>
  </div>
  
  <div>
    <div>
      <h3>單行輸入框</h3>
      <p><input v-model="text" />輸入文字:{{ text }}</p>
      <button @click="clearText">清空輸入框</button>
    </div>

    <div>
      <h3>單選框</h3>
      紅色<input type="radio" value="red" v-model="color2" />
      綠色<input type="radio" value="green" v-model="color2" />
      <div :class="color2">這是一段文字</div>
    </div>

    <div>
      <h3>多選框</h3>
      蘋果<input type="checkbox" value="apple" v-model="fruits" />
      香蕉<input type="checkbox" value="banana" v-model="fruits" />
      橘子<input type="checkbox" value="orange" v-model="fruits" />
      <p>選擇的水果: 
        <ul>
          <li v-for:="fruit in fruits">{{ fruit }}</li>
        </ul>
      </p>
    </div>

    <div>
      <h3>下拉式選框</h3>
      <select v-model="gender2">
        <option value="">請選擇</option>
        <option value="male">男</option>
        <option value="female">女</option>
      </select>
      <p >選擇的性別: {{ gender2 }}</p>
    </div>
  </div>
</template>
<style scoped>
.red{
  color:red;
}
.green{
  color:green;
}
</style>