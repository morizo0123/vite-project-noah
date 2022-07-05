<script lang="ts">
import { defineComponent } from "vue"
import CardListItem from './CardListItem.vue'
import { NewsData } from '../types/Types'

export default defineComponent({
  components: {
    CardListItem,
  },

  setup() {
    const newsData: NewsData[] = [
      {
        src: '/assets/thumbnail/thumbnail_01.jpg',
        href: '#',
        tag: 'グッズ',
        date: '2022.07.02',
        title: '【7･16日本武道館グッズ情報】拳王Tシャツ販売決定!!'
      },
      {
        src: '/assets/thumbnail/thumbnail_01.jpg',
        href: '#',
        tag: 'インフォメーション',
        date: '2022.07.02',
        title: '【7.2福島大会】選手欠場ならびに対戦カード変更のお知らせ(2日17:50更新)'
      },
      {
        src: '/assets/thumbnail/thumbnail_01.jpg',
        href: '#',
        tag: 'インフォメーション',
        date: '2022.07.01',
        title: '【15時45分から当日券発売！！】7月3日山形ビッグウイング大会チケット直前情報！【電子限...'
      },
      {
        src: '/assets/thumbnail/thumbnail_01.jpg',
        href: '#',
        tag: 'インフォメーション',
        date: '2022.06.30',
        title: '【6.30 放送】エフエム山形に清宮海斗が出演！【7.3山形ビッグウイング大会プロモーシ...'
      },
    ]

    return {
      newsData
    }
  }
})
</script>

<template>
  <ul class="card">
    <CardListItem :newsData="newsData" />
  </ul>
</template>

<style lang="scss">
.card {
  display: flex;
  flex-wrap: wrap;
  margin-left: -16px;
}
</style>