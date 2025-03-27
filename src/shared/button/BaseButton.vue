<template>
  <button :class="classes" :disabled="disabled">
    <slot name="leftIcon"></slot>
    <BaseText class="button__text" tagName="p" size="s">
      <slot></slot>
    </BaseText>
  </button>
</template>

<script setup lang="ts">
import BaseText from '../text/BaseText.vue'
interface Props {
  color?: 'primary' | 'secondary' | 'grayscale' | 'error'
  decoration?: 'default' | 'outline' | 'none'
  size?: 'L' | 'M' | 'S'
  disabled?: boolean
}

const props = defineProps<Props>()

const { color = 'primary', decoration = 'default', size = 'M', disabled = false } = props

const classes = ['button', `size--${size}`, `decoration--${decoration}`, `color--${color}`]
</script>

<style scoped>
.button {
  display: flex;
  align-items: center;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  width: 100%;
}
.button.size--M {
  padding: 8px;
  gap: 8px;
}
.button.color--secondary {
  background-color: var(--main-secondary);
  color: var(--main-on-secondary);
}
.button__text {
  width: 100%;
  text-align: center;
}
</style>
