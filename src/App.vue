<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import GridDemo from "./components/gridDemo.vue";
import {ref} from "vue";
import SwipeCellDemo from "./components/SwipeCellDemo.vue";

const show = ref();
const select = (v:string) => {
  show.value = v;
}
</script>

<template>
  <div class="">
<!--    <t-button theme="primary" @click="select('popup')">popup</t-button>-->
<!--    <t-button theme="primary" @click="select('grid-item')">grid-item</t-button>-->
<!--    <t-button theme="primary" @click="select('SwipeCell')">SwipeCell</t-button>-->
  </div>
<!--  <p>1. 查看popup问题请点击popup按钮</p>-->
<!--  <p>2. 查看grid-item问题请点击grid-item按钮</p>-->


<!--  <HelloWorld v-if="show === 'popup'" />
  <GridDemo v-if="show === 'grid-item'" />-->
  <SwipeCellDemo />
</template>

<style scoped>
</style>
