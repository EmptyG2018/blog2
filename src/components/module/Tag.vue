<template>
  <span
    class="vk-tag"
    :class="[
      size === 'small' ? 'vk-tag-sm' : size === 'large' ? 'vk-tag-lg' : '',
      selected ? 'vk-tag-selected' : '',
    ]"
    @click="emits('click')"
    >{{ label
    }}<span v-if="closable" class="vk-tag-close" @click="emits('close')"
      >×</span
    ></span
  >
</template>
<script setup lang="ts">
withDefaults(
  defineProps<{
    label: string;
    value: number;
    selected: boolean;
    size: 'default' | 'small' | 'large';
    closable: boolean;
  }>(),
  {
    selected: false,
    size: 'default',
    closable: false,
  }
);
const emits = defineEmits<{
  (e: 'click'): void;
  (e: 'close'): void;
}>();
</script>

<style lang="less" scoped>
.vk-tag {
  vertical-align: top;
  display: inline-block;
  white-space: nowrap;
  padding: 8px 12px;
  color: #8590a6;
  font-size: 12px;
  line-height: 1;
  border-radius: 2px;
  background-color: #e8eaed;
  margin: 3px 6px 3px 0;
}
.vk-tag.vk-tag-sm {
  font-size: 12px;
  padding: 6px 8px;
  margin: 2px 4px 2px 0;
}
.vk-tag.vk-tag-lg {
  font-size: 14px;
  padding: 10px 16px;
  margin: 4px 8px 4px 0;
}
.vk-tag.vk-tag-selected {
  background-color: #ecf5ff;
  color: #0084ff;
}
.vk-tag-close {
  display: inline-block;
  margin-left: 6px;
  cursor: pointer;
}
</style>
