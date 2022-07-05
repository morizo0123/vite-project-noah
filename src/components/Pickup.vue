<script lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Pagination, Navigation } from "swiper"
import 'swiper/css'
import "swiper/css/pagination"
import "swiper/css/navigation"

export default {
  components: {
    Swiper,
    SwiperSlide
  },

  setup() {
    return {
      modules: [Autoplay, Pagination, Navigation],
    }
  }
}
</script>

<template>
  <section class="pickup">
    <header class="pickup__header">
      <h2 class="pickup__header-title">pickup</h2>
    </header>

    <div class="pickup__body">
      <Swiper
        class="pickup__slide"
        :slidesPerView="3"
        :spaceBetween="16"
        :loop="true"
        :autoplay="{
          delay: 5000,
          disableOnInteraction: false, // ユーザーが操作しても自動再生を止めない
        }"
        :pagination="{
          clickable: true,
        }"
        :modules="modules"
      >
        <swiper-slide>
          <div class="pickup__banner">
            <a href="#">
              <img src="/assets/banner/banner_schedule_320_160.jpg" alt="">
            </a>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="pickup__banner">
            <a href="#">
              <img src="/assets/banner/banner_schedule_320_160.jpg" alt="">
            </a>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="pickup__banner">
            <a href="#">
              <img src="/assets/banner/banner_schedule_320_160.jpg" alt="">
            </a>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="pickup__banner">
            <a href="#">
              <img src="/assets/banner/banner_schedule_320_160.jpg" alt="">
            </a>
          </div>
        </swiper-slide>
      </Swiper>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.pickup {
  &__header {
    background-color: #009740;
    text-align: center;
  }

  &__header-title {
    color: #fff;
    font-size: 32px;
    font-weight: bold;
    padding: 8px 0;
    letter-spacing: .1em;
    text-align: center;
    text-transform: uppercase;
  }

  &__body {
    padding: 40px;
  }

  &__slide {
    width: 800px;

    img {
      width: 100%;
    }
  }
}
</style>