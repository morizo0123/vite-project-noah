<script lang="ts">
import { defineComponent } from "vue"

type HeaderData = {
  name: string;
  url: string;
  share: Array<string>;
  navLeft: Array<{title: string, href: string}>;
  navRight: Array<{title: string, href: string}>;
}

/*
interface HeaderData {
  name: string;
  share: Array<string>;
  navLeft: Array<{title: string, href: string}>;
  navRight: Array<{title: string, href: string}>;
}
*/

export default defineComponent({
  setup() {
    const headerData: HeaderData = {
      name: 'プロレスリング・ノア',
      url: 'https://www.noah.co.jp/',
      share: [
        'twitter', 'facebook', 'insta', 'tiktok', 'youtube', 'note',
      ],
      navLeft: [
        {
          'title': 'ニュース',
          'href': '#',
        },
        {
          'title': 'スケジュール/チケット',
          'href': '#',
        },
        {
          'title': '試合結果',
          'href': '#',
        },
        {
          'title': '選手紹介',
          'href': '#',
        }
      ],
      navRight: [
        {
          'title': 'グッズ',
          'href': '#',
        },
        {
          'title': 'Youtube',
          'href': '#',
        },
        {
          'title': 'ファンクラブ',
          'href': '#',
        },
        {
          'title': 'NOAHとは',
          'href': '#',
        },
      ]
    }

    return {
      headerData,
    }
  }
})
</script>

<template>
  <header class="global-header">
    <div class="global-header__inner">
      <h1 class="global-header__logo">
        <a :href="headerData.url" target="_blank" rel="noopener noreferrer">
          <img src="/assets/logo_noah.svg" :alt="headerData.name">
        </a>
      </h1>

      <ul class="global-header__sns">
        <li class="global-header__sns-item" v-for="(v, i) in headerData.share" :key="i"><a href="#"><img :src="`/assets/icon/icon_${v}.png`" :alt="v"></a></li>
      </ul>

      <nav class="global-header__nav">
        <ul class="global-header__list">
          <li class="global-header__item" v-for="(v, i) in headerData.navLeft" :key="i">
            <a :href="v.href">{{v.title}}</a>
          </li>
        </ul>

        <ul class="global-header__list">
          <li class="global-header__item" v-for="(v, i) in headerData.navRight" :key="i">
            <a :href="v.href">{{v.title}}</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style lang="scss">
.global-header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 100;
  width: 100%;

  &__inner {
    background-color: #fff;
    padding-top: 10px;
    position: relative;
  }

  // logo ------------------------
  &__logo {
    position: absolute;
    top: 6px;
    left: 50%;
    transform: translateX(-50%);

    a {
      display: inline-block;
    }

    img {
      width: 100px;
      height: auto;
    }
  }

  // sns ------------------------
  &__sns {
    display: flex;
    justify-content: flex-end;
    width: 990px;
    margin: 0 auto 10px;
  }

  &__sns-item {
    margin: 0 4px;

    a {
      display: inline-block;

      &:hover {
        opacity: .8;
      }
    }

    img {
      width: auto;
      height: 20px;
    }
  }

  // nav  ------------------------
  &__nav {
    display: flex;
    justify-content: center;
    background-color: #009740;
  }

  &__list + &__list {
    margin-left: 164px;
  }

  &__list {
    display: flex;
    width: 50%;

    &:nth-child(1) {
      justify-content: flex-end;
    }
  }

  &__item {
    a {
      display: flex;
      align-items: center;
      color: #fff;
      font-size: 14px;
      font-weight: bold;
      height: 45px;
      padding: 0 8px;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>