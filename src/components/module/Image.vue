<template>
  <div
    class="vk-image"
    :class="{ 'vk-image-block': block }"
    :style="{ width: `${width}px`, height: `${height}px` }"
  >
    <img ref="img" :src="src" :alt="alt" :style="{ objectFit: fit }" />
    <slot name="placeholder"></slot>
    <slot name="error"></slot>
  </div>
</template>

<script setup lang="ts">
withDefaults(
  defineProps<{
    block: boolean;
    width: number;
    height: number;
    src: string;
    fit:
      | 'contain'
      | 'initial'
      | 'cover'
      | 'fill'
      | 'inherit'
      | 'initial'
      | 'none'
      | 'revert'
      | 'scale-down'
      | 'unset';
    alt: string;
  }>(),
  {
    block: false,
    fit: 'initial',
  }
);
</script>

<style lang="less" scoped>
.vk-image {
  position: relative;
  display: inline-block;
  vertical-align: top;
  overflow: hidden;
  border-radius: 4px;
}
.vk-image.vk-image-block {
  display: block;
  width: 100%;
}
.vk-image img {
  display: block;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}
</style>
