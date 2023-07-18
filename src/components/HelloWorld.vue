<template>
  <div class="popup-demo">
    <t-button
        block
        variant="outline"
        theme="primary"
        size="large"
        @click="visible = true"
    >底部弹出层-带标题及操作 popup</t-button>
    <t-list>
      <t-cell v-for="item in 20" :key="item" align="middle">
        <span class="cell">{{ item }}</span>
      </t-cell>
    </t-list>
    <t-popup v-model="visible" placement="bottom" style="height: 258px">
      <div class="header">
        <div class="btn btn--cancel" aria-role="button" @click="onHide">
          取消
        </div>
        <div class="title">标题文字</div>
        <div class="btn btn--confirm" aria-role="button" @click="onHide">
          确定
        </div>
      </div>
      <t-button
          block
          variant="outline"
          theme="primary"
          size="large"
          @click="visible1 = true"
      >底部弹出层-带标题及操作 popup1</t-button>
    </t-popup>
    <t-popup v-model="visible1" placement="bottom" style="height: 258px">
      <div class="header">
        <div class="btn btn--cancel" aria-role="button" @click="onHide1">
          取消
        </div>
        <div class="title">标题文字</div>
        <div class="btn btn--confirm" aria-role="button" @click="onHide1">
          确定
        </div>
      </div>

      <p>点击取消，滚动条可以滚动</p>
    </t-popup>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const visible = ref(false);
const visible1 = ref(false);
const onHide = () => (visible.value = false);
const onHide1 = () => (visible1.value = false);
</script>

<style lang="less" scoped>
.popup-demo {
  padding: 0 16px;
}

.header {
  display: flex;
  align-items: center;
  height: 116rpx;
}

.title {
  flex: 1;
  text-align: center;
  font-weight: 600;
  font-size: 18px;
}

.btn {
  font-size: 16px;
  padding: 16px;
}

.btn--cancel {
  color: rgba(0, 0, 0, 0.6);
}

.btn--confirm {
  color: #0052d9;
}
</style>
>
