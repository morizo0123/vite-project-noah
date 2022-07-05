<script lang="ts">
import { defineComponent } from "vue"
import SectionHeader from "./SectionHeader.vue"

type ChampionData = {
  weight: 'ヘビー級' | 'ナショナル王座' | 'ジュニアヘビー級' | 'タッグチーム' | 'ジュニアヘビータッグチーム' | 'オープン・ザ・トライアングルゲート';
  name: string;
  src: string;
  alt: string;
  empty?: boolean;
}

export default defineComponent({
  components: {
    SectionHeader
  },

  setup() {
    const championSingleData: ChampionData[] = [
      {
        weight: 'ヘビー級',
        name: '小島聡',
        src: '/assets/picture/picture_kojima.jpg',
        alt: 'ヘビー級チャンピオン 小島聡',
      },
      {
        weight: 'ナショナル王座',
        name: '船木誠勝',
        src: '/assets/picture/picture_funaki.jpg',
        alt: 'ナショナル王座チャンピオン 船木誠勝',
      },
      {
        weight: 'ジュニアヘビー級',
        name: 'HAYATA',
        src: '/assets/picture/picture_hayata.jpg',
        alt: 'ジュニアヘビー級チャンピオン HAYATA',
      },
    ]
    const championTagData: ChampionData[] = [
      {
        weight: 'タッグチーム',
        name: 'マイケル・エルガン<br>マサ北宮',
        src: '/assets/picture/picture_heavy_tag.jpg',
        alt: 'タッグチームチャンピオン マイケル・エルガン / マサ北宮',
      },
      {
        weight: 'ジュニアヘビータッグチーム',
        name: '小川良成<br>クリス・リッジウェイ',
        src: '/assets/picture/picture_junior_tag.jpg',
        alt: 'タッグチームチャンピオン 小川良成 / クリス・リッジウェイ',
      },
      {
        weight: 'オープン・ザ・トライアングルゲート',
        name: '',
        src: '',
        alt: '',
        empty: true,
      },
    ]

    return {
      championSingleData,
      championTagData
    }
  }
})
</script>

<template>
  <section class="champion">
    <SectionHeader icon="champion" title="チャンピオン(GHC)" />

    <div class="champion__body">
      <section class="champion__single">
        <h3 class="champion__belt">シングル</h3>
        <ul class="champion__list">
          <li class="champion__item" v-for="(v, i) in championSingleData" :key="i">
            <h4 class="champion__name">
              <p class="weight">{{ v.weight }}</p>
              <p class="name"><span>{{ v.name }}</span></p>
            </h4>
            <figure class="champion__figure">
              <img :src="v.src" :alt="v.alt">
            </figure>
          </li>
        </ul>
      </section>

      <section class="champion__tag">
        <h3 class="champion__belt">タッグ</h3>
        <ul class="champion__list">
          <li class="champion__item" v-for="(v, i) in championTagData" :key="i">
            <h4 class="champion__name">
              <p class="weight">{{ v.weight }}</p>
              <p class="name"><span v-html="v.name"></span></p>
            </h4>
            <figure class="champion__figure">
              <img :src="v.src" :alt="v.alt">
            </figure>

            <template v-if="v.empty">
              <p class="champion__note">オープン・ザ・トライアングルゲート王座は、DRAGON GATEが管理、認定している王座。</p>
            </template>
          </li>
        </ul>
      </section>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.champion {
  padding: 60px 0;

  &__single {
    margin-bottom: 28px;
  }

  &__belt {
    border-bottom: 2px solid #303030;
    display: inline-block;
    font-size: 20px;
    margin-bottom: 14px;
    padding-bottom: 4px;
  }

  &__body {
    width: 1260px;
    margin: 0 auto;
  }

  &__list {
    display: flex;
    margin-left: -16px;
  }

  &__item {
    width: calc(33.3% - 16px);
    margin-left: 16px;
  }

  &__name {
    background-color: #303030;
    color: #fff;
    font-size: 15px;
    min-height: 78px;
    padding: 16px;
    line-height: 1.4;

    .weight {
      border-bottom: 1px solid #fff;
      margin-bottom: 8px;
      padding-bottom: 8px;
    }
  }

  &__figure {
    img {
      max-width: 100%;
    }
  }

  &__note {
    line-height: 1.5;
  }
}
</style>