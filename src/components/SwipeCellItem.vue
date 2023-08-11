<template>
      <div class="">{{item.text}} {{item.icon}}</div>

</template>

<script lang="ts" setup>

const props = defineProps({
  item:{},
})



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
