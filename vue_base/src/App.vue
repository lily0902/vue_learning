<script setup>
import { ref } from 'vue'
import formSet from './form.vue'
import NavCom from './Nav.vue'
let content = ref('網站的內容')
let handler = function () {
  content.value = '網站的內容已經改變'
}
let data = 'amy'
let htmlData = '<u>hello</u>'
let name = 'content'
let color = false
let level = 0
let topics = ['HTML', 'CSS', 'JavaScript', 'Vue.js']
let topicsKey = { html: 'HTML', css: 'CSS', js: 'JavaScript', vue: 'Vue.js' }
let clickHandler = function () {
  console.log('點擊了')
}
let mouseoverHandler = function () {
  console.log('滑鼠移入')
}

let subtitle = ref('這是網站的副標題')
let updateSubtitle = function () {
  subtitle.value = '這是新的副標題'
}
let visible = ref(true)
let hide = function () {
  visible.value = false
}
let show = function () {
  visible.value = true
}
</script>

<template>
  <NavCom v-if="visible" title="這是標題一" :subtitle="subtitle"></NavCom>
  <button @click="hide">隱藏</button>
  <button @click="show">顯示</button>

  <main>基本的主內容</main>
  <p>{{ data }}你好阿</p>
  <div v-html="htmlData.toUpperCase()"></div>
  <div v-bind:class="name">操作標籤的屬性</div>
  <div :class="color ? 'dark' : 'light'">操作標籤的屬性</div>

  <main>
    <div v-if="level === 3">大神</div>
    <div v-else-if="level === 2">資深</div>
    <div v-else-if="level === 1">中階</div>
    <div v-else>
      <div>入門</div>
      <ul>
        <li v-for:="(topic, index) in topics">{{ index }}-{{ topic }}</li>
        <li v-for:="(value, key) in topicsKey">{{ key }}:{{ value }}</li>
      </ul>
    </div>

    <div>{{ content }}</div>
    <button @click="handler">點我</button>

    <span @click="clickHandler" @mouseover="mouseoverHandler">文字</span>
    <a href="https://www.youtube.com/" @click.prevent>課程網站</a>

    <br /><br />
    <div>{{ subtitle }}</div>
    <formSet bgr="pink" color="blue" @update="updateSubtitle"></formSet>
  </main>
</template>
<style scoped>
main {
  background-color: #dddddd;
}
.content {
  color: blue;
}
.dark {
  color: black;
}
.light {
  color: #888888;
}
</style>
