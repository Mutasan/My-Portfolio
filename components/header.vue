<template>
  <div class="header">
    <span class="header__title">キタムラ's Portfolio</span>
    <div class="flex-grow-1" />
    <a class="header__content">About Me</a>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({})
</script>
<style lang='scss' scoped>
.header {
  display: flex;
  height: 80px;
  background-color: $color-black;
  &__title {
    margin: auto 20px;
    color: $color-white;
  }
  &__content {
    margin: auto 20px;
  }
}
</style>