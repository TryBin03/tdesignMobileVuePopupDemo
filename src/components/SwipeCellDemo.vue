<template>
<div style="background: #888888">
  <div class="trade-item" :key="index" v-for="(item, index) in list">
    <swipe-cell-item  :item="item" @delete="deleteItem"></swipe-cell-item>
  </div>
</div>
  <p>1.向左滑动，点击删除</p>
  <p>2.点击确认删除</p>
  <p>3.删除成功，但是还是会显示删除按钮</p>
</template>

<script lang="ts" setup>
import {ref} from "vue";
import SwipeCellItem from "./SwipeCellItem.vue";

const list = ref([
  {text: "点赞", icon: "👍"},
  {text: "投币", icon: "🪙"},
  {text: "点赞", icon: "⭐"}
])

const handoff = () => {
  list.value = [
    {text: "1", icon: "🔢"},
    {text: "2", icon: "🔢🔢"},
    {text: "3", icon: "🔢🔢🔢"}
  ]
}

const deleteItem = (text) => {
  var index = list.value.findIndex(i => i.text == text);
  list.value.splice(index,1)
}
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
