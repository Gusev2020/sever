<template>
  <div
    :class="[
      'field',
      `disabled--${disabled}`,
      `size--${size}`,
      `left-icon_${Boolean(slots.leftIcon)}`,
      `right-icon_${Boolean(slots.rightIcon)}`,
    ]"
  >
    <slot name="label"></slot>
    <div class="field__container">
      <div v-if="slots.leftIcon" class="field__left-icon" @click="onSubmit">
        <slot name="leftIcon"></slot>
      </div>
      <input
        class="field__input"
        type="text"
        :placeholder="placeholder"
        :disabled="disabled"
        @input="onChange(($event.target as HTMLInputElement)?.value)"
        @keyup.enter="onSubmit"
      />
      <div v-if="slots.rightIcon" class="field__right-icon" @click="onSubmit">
        <slot name="rightIcon"></slot>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useSlots } from 'vue'
interface Props {
  disabled?: boolean
  size?: 'l' | 'm'
  placeholder?: string
  onChange?: (value: string) => void
  onSubmit?: () => void
}

const slots = useSlots()
const props = defineProps<Props>()
const { disabled = false, size = 'm', placeholder, onChange = () => {} } = props
</script>

<style scoped>
.field:deep(.typography) {
  color: var(--grayscale-hard);
}

.field__input {
  width: 100%;
  border-radius: 4px;
  border: 1px solid var(--grayscale-hard);
  background-color: var(--main-surface);
  color: var(--main-on-surface);
  transition: 0.3s ease-in-out;
}

.field__input:focus {
  border: 1px solid var(--main-secondary);
  box-shadow: var(--shadow-secondary-m);
  caret-color: var(--main-secondary);
}

.field__input:disabled {
  border: 1px solid var(--grayscale-light);
  background-color: var(--grayscale-lightest);
}

.field__input::placeholder {
  color: var(--grayscale-hard);
}

.field.size--m .field__input {
  padding: 8px 16px;
  font-size: 16px;
}

.field.size--l .field__input {
  padding: 12px 16px;
  font-size: 24px;
}

.field__label {
}

.field__container {
  position: relative;
}

/* Позиционирование иконок */
.field__left-icon,
.field__right-icon {
  position: absolute;
  cursor: pointer;
}

/* позиционарование для компонента M размера */

.field.left-icon_true.size--m .field__left-icon {
  top: 8px;
  left: 8px;
}

.field.left-icon_true.size--m .field__input {
  padding-left: 40px;
}

.field.right-icon_true.size--m .field__right-icon {
  top: 8px;
  right: 8px;
}

.field.right-icon_true.size--m .field__input {
  padding-right: 40px;
}

/* позиционарование для компонента L размера */

.field.left-icon_true.size--l .field__left-icon {
  top: 8px;
  left: 8px;
  padding: 6px;
}

.field.left-icon_true.size--l .field__input {
  padding-left: 56px;
}

.field.right-icon_true.size--l .field__right-icon {
  top: 8px;
  right: 8px;
  padding: 6px;
}

.field.right-icon_true.size--l .field__input {
  padding-right: 56px;
}
</style>
