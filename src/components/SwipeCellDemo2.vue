<template>
  <div>
    <t-swipe-cell v-for="(item, index) in list" ref="cell" :key="item.text">
      <t-cell :title="item.text + item.icon + index" note="辅助信息"></t-cell>
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
</template>

<script setup lang="ts">
import { ref } from 'vue';

const cell = ref();

const handleDelete = (text: string) => {
  const index = list.value.findIndex((i) => i.text === text);
  cell.value[index].showSure('sure-delete');
};

const list = ref([
  { text: '点赞1', icon: '👍' },
  { text: '投币', icon: '🪙' },
  { text: '点赞2', icon: '⭐' },
]);

const handleSureDelete = (text: any) => {
  const index = list.value.findIndex((i) => i.text === text);
  list.value.splice(index, 1);
};
</script>

<style scoped lang="less">
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
