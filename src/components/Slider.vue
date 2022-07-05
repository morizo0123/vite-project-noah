<script lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Pagination, Navigation } from "swiper"
import 'swiper/css'
import "swiper/css/pagination"
import "swiper/css/navigation"

export default {
  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    const onSwiper = (swiper: any) => {
      console.log(swiper);
    };

    const onSlideChange = () => {
      console.log('slide change');
    };

    return {
      onSwiper,
      onSlideChange,
      modules: [Autoplay, Pagination, Navigation],
    };
  }
}
</script>

<template>
  <swiper
    class="slide"
    :slidesPerView="1.2"
    :centeredSlides="true"
    :spaceBetween="30"
    :loop="true"
    :autoplay="{
      delay: 5000,
      disableOnInteraction: false, // ユーザーが操作しても自動再生を止めない
    }"
    :pagination="{
      clickable: true,
    }"
    :modules="modules"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <swiper-slide>
      <img src="/assets/slider/slider_img_01.jpg" alt="">
    </swiper-slide>
    <swiper-slide>
      <img src="/assets/slider/slider_img_02.jpg" alt="">
    </swiper-slide>
    <swiper-slide>
      <img src="/assets/slider/slider_img_03.jpg" alt="">
    </swiper-slide>
    <swiper-slide>
      <img src="/assets/slider/slider_img_04.jpg" alt="">
    </swiper-slide>
  </swiper>
</template>

<style lang="scss" scoped>
.slide img {
  width: 100%;
}
</style>