<template>
  <component
    :is="props.tagName"
    :class="['typography', size ? `size--${size}` : '', bold ? 'bold' : '', `tag_${tagName}`]"
  >
    <slot></slot>
  </component>
</template>
<script setup lang="ts">
interface Props {
  tagName: 'p' | 'h1' | 'h2' | 'h3' | 'h4' | 'h5'
  bold?: boolean
  size?: 'xs' | 's' | 'm' | 'l' | 'xl'
}

const props = defineProps<Props>()
</script>

<style scoped>
.typography {
  font-style: normal;
  line-height: 150%;
  font-family: 'Rubik', sans-serif;
}
.bold {
  font-weight: 700;
}

.size--xs {
  font-size: 12px;
}
.size--s {
  font-size: 16px;
}
.size--m {
  font-size: 18px;
}
.size--l {
  font-size: 24px;
}
.size--xl {
  font-size: 36px;
}
.tag_h1 {
  font-size: 64px;
}
.tag_h2 {
  font-size: 48px;
}
.tag_h3 {
  font-size: 36px;
}
.tag_h4 {
  font-size: 24px;
}
.tag_h5 {
  font-size: 18px;
}

@media screen and (max-width: 768px) {
  .size--xs {
    font-size: 8px;
  }
  .size--s {
    font-size: 12px;
  }
  .size--m {
    font-size: 14px;
  }
  .size--l {
    font-size: 18px;
  }
  .size--xl {
    font-size: 24px;
  }
  .tag_h1 {
    font-size: 48px;
  }
  .tag_h2 {
    font-size: 36px;
  }
  .tag_h3 {
    font-size: 24px;
  }
  .tag_h4 {
    font-size: 20px;
  }
  .tag_h5 {
    font-size: 16px;
  }
}
</style>
