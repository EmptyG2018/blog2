<template>
  <div
    class="vk-card"
    :class="{ 'vk-card-block': block }"
    :style="{ width: `${width}px`, height: `${height}px` }"
  >
    <div
      class="vk-card-content"
      :class="[
        theme === 'x'
          ? 'vk-card-theme-x'
          : theme === 'y'
          ? 'vk-card-theme-y'
          : '',
      ]"
    >
      <slot></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
withDefaults(
  defineProps<{
    theme: 'xy' | 'x' | 'y';
    block: boolean;
    width: number;
    height: number;
  }>(),
  {
    theme: 'xy',
    block: false,
  }
);
</script>

<style lang="less" scoped>
.vk-card {
  box-sizing: border-box;
  display: inline-block;
  vertical-align: top;
  background-color: #fff;
  width: 286px;
  border-radius: 4px;
  margin-bottom: 10px;
}
.vk-card-block {
  display: block;
  width: 100%;
}
.vk-card-content {
  box-sizing: border-box;
  padding: 20px;
  width: 100%;
  height: 100%;
}
.vk-card-theme-x {
  padding: 0 20px;
}
.vk-card-theme-y {
  padding: 20px 0;
}
</style>
