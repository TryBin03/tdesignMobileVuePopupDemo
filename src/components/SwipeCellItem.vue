<template>

    <t-swipe-cell ref="cell" @opened="opened">
      <div class="">{{item.text}} {{item.icon}}</div>
      <template #right>
        <div class="btn delete-btn" @click="handleDelete()">
          删除
        </div>
      </template>
      <template #left>
        <div class="btn notCounted-btn">
          不计入总账
        </div>
        <div class="btn edit-btn">
          编辑
        </div>
      </template>
      <template #sure-delete>
        <div class="btn delete-btn" @click="handleSureDelete(item)">确认删除？</div>
      </template>
    </t-swipe-cell>

</template>

<script lang="ts" setup>
import {ref} from "vue";

const props = defineProps({
  item:{}
})
const emit = defineEmits(['delete'])

const cell = ref();

const handleDelete = () => {
  cell.value.showSure("sure-delete");
}
const handleSureDelete = (item) => {

  emit('delete', item.text)
}
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
