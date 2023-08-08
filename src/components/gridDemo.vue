<template>
  <t-grid :column="3" class="grid-demo">
    <t-grid-item :text="item.text"  v-for="(item, index) in list">
      <template #image>
        <div :key="index" class="icon-wrapper">
          {{ item.icon }}
        </div>
      </template>
    </t-grid-item>
  </t-grid>

  <t-button theme="primary" @click="handoff">点击切换 t-grid-item 内容</t-button>
  <p>出现问题，icon没有切换(image中的内容)</p>
  <p>切换后应当渲染的数据 [
    {text: "1", icon: "🔢"},
    {text: "2", icon: "🔢🔢"},
    {text: "3", icon: "🔢🔢🔢"}
    ]</p>

</template>

<script lang="ts" setup>
import {ref} from "vue";

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
</script>
<style scoped lang="less">
.icon-wrapper {
  background: #eee;
  border-radius: 6px;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
