<template>
  <div style="width: 100vw">
    <p>左右滑动有效</p>
    <p>ps:请移动端操作</p>
      <t-swipe-cell v-for="(item, index) in list" ref="cell" :key="item.text" :opened="opened" @change="handleChange">
        <t-cell :title="item.text + item.icon + index" note="辅助信息"></t-cell>
        <template #right>
          <div class="btn delete-btn" @click="handleDelete(item.text)">删除</div>
        </template>
        <template #left>
          <div class="btn notCounted-btn" @click="notGeneral(item.text)">不计入总账</div>
          <div class="btn edit-btn">编辑</div>
        </template>
        <template #sure-delete>
          <div class="btn delete-btn" @click="handleSureDelete(item.text)">确认删除？</div>
        </template>
      </t-swipe-cell>
    <t-button @click="visible = true">弹出popup</t-button>
    <t-popup :visible="visible" :placement="'bottom'">
      <p>左右滑动无效</p>
      <t-button @click="visible = false">收起popup</t-button>
        <t-swipe-cell v-for="(item, index) in list" ref="cell" :key="item.text" :opened="opened" @change="handleChange">
          <t-cell :title="item.text + item.icon + index" note="辅助信息"></t-cell>
          <template #right>
            <div class="btn delete-btn" @click="handleDelete(item.text)">删除</div>
          </template>
          <template #left>
            <div class="btn notCounted-btn" @click="notGeneral(item.text)">不计入总账</div>
            <div class="btn edit-btn">编辑</div>
          </template>
          <template #sure-delete>
            <div class="btn delete-btn" @click="handleSureDelete(item.text)">确认删除？</div>
          </template>
        </t-swipe-cell>
    </t-popup>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const cell = ref();
const opened = ref([false, false]);

const handleDelete = (text: string) => {
  const index = list.value.findIndex((i) => i.text === text);
  cell.value[index].showSure('sure-delete');
};

const list = ref([
  { text: '点赞1', icon: '👍' },
  { text: '投币', icon: '🪙' },
  { text: '点赞2', icon: '⭐' },
]);

const visible = ref(false);

const handleSureDelete = (text: any) => {
  const index = list.value.findIndex((i) => i.text === text);
  list.value.splice(index, 1);
};

const notGeneral = (text: any) => {
  console.log("111")
  const index = list.value.findIndex((i) => i.text === text);
  console.log(cell.value[index]);
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
