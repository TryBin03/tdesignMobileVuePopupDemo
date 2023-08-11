<template>
<div style="background: #888888">
    <t-swipe-cell v-for="(item, index) in list" :key="item.text" ref="tradeList" :opened="opened" @change="handleChange">
      <div class="trade-item" >
        <swipe-cell-item  :item="item"></swipe-cell-item>
      </div>
      <template #right>
        <div class="btn delete-btn" @click="handleDelete(item.text)">删除</div>
      </template>
      <template #left>
        <div class="btn notCounted-btn">不计入总账</div>
        <div class="btn edit-btn">编辑</div>
      </template>
      <template #sure-delete>
        <div class="btn delete-btn" @click="handleSureDelete(item.text)">确认删除？</div>
      </template>
    </t-swipe-cell>
</div>
  <p>1.向左滑动，点击删除</p>
  <p>2.点击确认删除</p>
  <p>3.删除成功，但是还是会显示删除按钮</p>
  <p>ps:请移动端操作</p>
</template>

<script lang="ts" setup>
import {ref} from "vue";
import SwipeCellItem from "./SwipeCellItem.vue";

const tradeList = ref()
const opened = ref([false, false]);

const list = ref([
  {text: "点赞", icon: "👍"},
  {text: "投币", icon: "🪙"},
  {text: "点赞", icon: "⭐"}
])

const handleDelete = (text: string) => {
  const index = list.value.findIndex((i) => i.text === text);
  tradeList.value[index].showSure('sure-delete');
}
const handleSureDelete = (text: string) => {
  var index = list.value.findIndex((i) => i.text === text);
  list.value.splice(index,1)
}


const notGeneral = (text: any) => {
  console.log("111")
  const index = list.value.findIndex((i) => i.text === text);
  opened.value[dir.value === 'left' ? 0 : 1] = false;
  // cell.value[index].opened[0] = false;
}
const dir = ref('right');

const handleChange = (d: string) => {
  console.log(d);
  if (d) {
    opened.value[d === 'left' ? 0 : 1] = true;
  } else {
    opened.value[0] = false;
    opened.value[1] = false;
  }
  dir.value = d;
};
</script>
<style scoped lang="less">
.trade-item{
  width: 300px;
}
.btn {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 80px;
  color: white;
  font-size: 14px;
}
.delete-btn {
  background-color: red;
}
.edit-btn {
  background-color: #747bff;
}
.notCounted-btn {
  background-color: #1e80ff;
}
</style>
