<script lang="ts">
import { defineComponent, PropType } from "vue"
import { NewsData } from '../types/Types'

export default defineComponent({
  // PropType<T>でアサーションすることによって、より詳細に型を宣言できます。
  props: {
    newsData: Array as PropType<NewsData[]>,
  },

  setup() {
    return {}
  }
})
</script>

<template>
  <li class="card__item" v-for="(v, i) in newsData" :key="i">
    <a :href="v.href" class="card__link">
      <img :src="v.src" alt="">
      <div class="card__body">
        <div class="card__tag-and-date">
          <p class="card__tag">{{ v.tag }}</p>
          <p class="card__date">{{ v.date }}</p>
        </div>
        <p class="card__title">{{ v.title }}</p>
      </div>
    </a>
  </li>
</template>

<style lang="scss">
.card {
  &__item {
    width: calc(33.3% - 16px);
    margin-bottom: 16px;
    margin-left: 16px;
  }

  &__link {
    display: block;

    img {
      max-width: 100%;
    }

    &:hover {
      opacity: .8;
    }
  }

  &__body {
    padding: 8px 0 0;
  }

  &__tag-and-date {
    display: flex;
    justify-content: space-between;
  }

  &__tag {
    display: inline-block;
    background-color: #000;
    color: #fff;
    font-size: 10px;
    margin-bottom: 4px;
    padding: 4px 8px;
  }

  &__date {
    color: #aaa;
    font-size: 10px;
  }

  &__title {
    font-size: 12px;
    line-height: 1.5;
  }
}
</style>