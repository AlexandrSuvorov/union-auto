<template>
  <button class="callback">
    <slot>Request a callback</slot>
  </button>
</template>

<script setup lang="ts">
</script>

<style lang="scss" scoped>
.callback {
  height: 55px;
  background: black;
  color: white;
  padding: 0 51px;
  border: none;
  cursor: pointer;
  font-size: 16px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: 'InterDisplayRegular', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: white;
}
</style>
