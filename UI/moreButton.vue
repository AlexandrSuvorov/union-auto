<template>
  <button class="callback">
    <slot/>
  </button>
</template>

<script setup lang="ts">

</script>

<style lang="scss" scoped>
.callback {
  height: 55px;
  background: transparent;
  color: white;
  padding: 23px 44px;
  border: 1px solid white;
  cursor: pointer;
  border-radius: 10px;
  font-size: 16px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: 'EurostileExtMed', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: white;
  backdrop-filter: blur(4px);
}
</style>
