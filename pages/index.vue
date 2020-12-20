<template>
  <div>
    <hello />
    <header-button />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

import HeaderButton from '@/components/molecules/HeaderButton.vue'
import Hello from '@/components/molecules/Hello.vue'

@Component({
  components: {
    HeaderButton,
    Hello,
  },
})
export default class Index extends Vue {}
</script>

<style scoped lang="scss"></style>
