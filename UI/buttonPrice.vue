<template>
  <button class="buttonPrice">
    <slot/>
  </button>
</template>

<script setup lang="ts">

</script>

<style lang="scss" scoped>
.buttonPrice {
  height: 45px;
  background: transparent;
  color: white;
  padding: 14px 83px;
  border: 1px solid black;
  cursor: pointer;
  border-radius: 8px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  color: black;
  backdrop-filter: blur(4px);
  font: 500 normal 12px/100% 'EurostileExtMed';
}
</style>
