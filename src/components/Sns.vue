<script lang="ts">
import { defineComponent, onMounted } from "vue"
import SectionHeader from "./SectionHeader.vue"

export default defineComponent({
  components: {
    SectionHeader
  },

  setup() {
    onMounted(() => {
      const tweetScript = document.createElement('script')
      tweetScript.setAttribute('src', 'https://platform.twitter.com/widgets.js')
      document.head.appendChild(tweetScript)
    })

    return {}
  }
})
</script>

<template>
  <section class="sns">
    <SectionHeader icon="sns" title="SNS" />

    <div class="sns__body">
      <ul class="sns__list">
        <li class="sns__item">
          <a class="twitter-timeline" data-width="300" data-height="600" data-theme="dark" href="https://twitter.com/noah_ghc?ref_src=twsrc%5Etfw">Tweets by noah_ghc</a>
        </li>
        <li class="sns__item">
          <a class="twitter-timeline" data-width="300" data-height="600" data-theme="dark" href="https://twitter.com/PKDX?ref_src=twsrc%5Etfw">Tweets by PKDX</a>
        </li>
        <li class="sns__item">
          <a class="twitter-timeline" data-width="300" data-height="600" data-theme="dark" href="https://twitter.com/Hideki55Suzuki?ref_src=twsrc%5Etfw">Tweets by Hideki55Suzuki</a>
        </li>
      </ul>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.sns {
  padding: 60px 0;

  &__body {
    width: 1260px;
    margin: 0 auto;
  }

  &__list {
    display: flex;
  }

  &__item {
    margin-right: 16px;
  }
}
</style>