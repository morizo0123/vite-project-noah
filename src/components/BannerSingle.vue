<script lang="ts">
import { defineComponent } from "vue"

export default defineComponent({
  setup() {
    const banner: string = '/assets/banner/banner_wrestleuniverse.png';

    return {
      banner
    }
  }
})
</script>

<template>
  <div class="banner-single">
    <a href="#">
      <img :src="banner" alt="">
    </a>
  </div>
</template>

<style lang="scss" scoped>
.banner-single {
  padding: 40px;
  text-align: center;

  a {
    display: inline-block;

    &:hover {
      opacity: .8;
    }
  }
}
</style>