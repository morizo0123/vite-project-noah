<script lang="ts">
import { defineComponent, onMounted } from "vue"
import SectionHeader from './SectionHeader.vue'
import CardList from './CardList.vue'

type Tabs = {
  id: string;
  title: string;
  active: boolean;
}

export default defineComponent({
  components: {
    SectionHeader,
    CardList,
  },

  setup() {
    const tabs: Tabs[] = [
      {
        id: 'all',
        title: '全て',
        active: true,
      },
      {
        id: 'info',
        title: 'インフォ',
        active: false,
      },
      {
        id: 'media',
        title: 'メディア',
        active: false,
      },
      {
        id: 'event',
        title: 'イベント',
        active: false,
      },
      {
        id: 'goods',
        title: 'グッズ',
        active: false,
      }
    ]

    onMounted(() => {
      const tabs = Array.from(document.querySelectorAll('.tab__item'))
      tabs.forEach(tab => {
        tab.addEventListener('click', () => {

          tabs.forEach(tab => {
            tab.classList.remove('is-active')
          })
          tab.classList.add('is-active')
        })
      })
    })

    return {
      tabs,
    }
  }
})
</script>

<template>
  <section class="news">
    <SectionHeader icon="news" title="ニュース" />

    <div class="news__body">
      <div class="news__content">
        <div class="tab">
          <ul class="tab__list">
            <li
              class="tab__item"
              :class="{ 'is-active':tab.active }"
              v-for="(tab, index) in tabs" :key="index"
            >
              {{ tab.title }}
            </li>
          </ul>
        </div>

        <div class="panel">
          <CardList />
        </div>
      </div>

      <div class="news__aside">
        <div class="news__aside-banner">
          <a>
            <img src="/assets/banner/banner_line.jpg" alt="">
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.news {
  background-color: #161616;
  padding: 60px 0;

  &__body {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    width: 1260px;
    margin: 0 auto;
  }

  &__content {
    width: 920px;
    background-color: #fff;
  }

  &__aside {
    width: 320px;
  }
}


.tab {
  &__list {
    display: flex;
  }

  &__item {
    color: #fff;
    background: #bfbfbf;
    cursor: pointer;
    font-size: 12px;
    text-align: center;
    padding: 12px 0;
    width: 20%;

    &:hover {
      opacity: .8;
    }
  }

  &__item.is-active {
    background-color: #fff;
    color: #161616;
  }
}

.panel {
  background-color: #f7f7f7;
  padding: 16px;
}
</style>