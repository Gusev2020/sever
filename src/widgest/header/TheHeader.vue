<template>
  <header class="header">
    <Container>
      <div class="header__container">
        <Logo orientation="horizontal" colorful bgcolor="white" withText />
        <div class="header__catalog">
          <BaseButton color="secondary">
            <template v-slot:leftIcon>
              <BaseIcon type="menu" />
            </template>
            Каталог
          </BaseButton>
        </div>
      </div>
    </Container>
  </header>
</template>
<script setup lang="ts">
import Container from '@/shared/container/BaseContainer.vue'
import Logo from '@/shared/logo/Logo.vue'
import BaseButton from '@/shared/button/BaseButton.vue'
import BaseIcon from '@/shared/icon/BaseIcon.vue'
</script>
<style scoped>
.header {
  position: sticky;
  top: 0;
  left: 0;
  background: var(--main-surface);
  box-shadow: var(--shadow-default-s);
}
.header__container {
  display: flex;
  align-items: center;
  height: 72px;
}
.header__catalog {
  width: 140px;
  margin-left: 40px;
}
</style>
