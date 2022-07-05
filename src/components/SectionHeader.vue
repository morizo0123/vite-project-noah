<script lang="ts">
import { defineComponent, PropType } from "vue"

export default defineComponent({
  // PropType<T>でアサーションすることによって、より詳細に型を宣言できます。
  props: {
    icon: String as PropType<'news' | 'champion' | 'video' | 'sns'>,
    title: String as PropType<'ニュース' | 'チャンピオン(GHC)' | '動画' | 'SNS'>, // リテラル型の合併
  },

  setup() {
    return {}
  }
})
</script>

<template>
  <header class="section-header">
    <h2 class="section-header__title">
      <i :class="`icon-${icon}`"></i>
      {{ title }}
    </h2>
  </header>
</template>

<style lang="scss">
.section-header {
  width: 1260px;
  border-left: 4px solid #009740;
  margin: 0 auto 24px;
  padding-left: 16px;

  &__title {
    color: #fff;
    font-size: 36px;
    font-weight: bold;
  }
}

.champion,
.sns {
  .section-header__title {
    color: #000;
  }
}
</style>