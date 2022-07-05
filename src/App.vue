<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue'
import Layout from './components/Layout.vue'
import Slider from './components/Slider.vue'
import BannerSingle from './components/BannerSingle.vue'
import Pickup from './components/Pickup.vue'
import News from './components/News.vue'
import Champion from './components/Champion.vue'
import Sns from './components/Sns.vue'
import Modal from './components/Modal.vue'

export default defineComponent({
  name: "App",

  components: {
    Layout,
    Slider,
    BannerSingle,
    Pickup,
    News,
    Champion,
    Sns,
    Modal
  },

  setup() {
    let isLoading = ref<boolean>(true)

    onMounted(() => {
      const loading = document.querySelector<HTMLElement>('.loading')

      new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve(loading?.classList.add('active'));
          console.log('1')
        }, 2000)
      }).then(() => {
        setTimeout(() => {
          loading?.classList.add('fadeout')
          console.log('2')
        }, 3000)
      }).then(() => {
        setTimeout(() => {
          isLoading.value = false;
          console.log('3')
        }, 4000)
      }).catch((e) => {
        console.log(e)
      })
    })

    const modalVisible = ref<boolean>(true)

    const showModal = () => {
      modalVisible.value = true
    }

    const closeModal = () => {
      modalVisible.value = false
    }

    return {
      isLoading,
      modalVisible,
      showModal,
      closeModal,
    }
  },
});
</script>

<template>
  <transition name="opacity">
    <template v-if="isLoading">
      <div class="loading">
        <img src="/assets/logo_noah.svg" alt="">
      </div>
    </template>
    <template v-else>
      <Layout>
        <Slider />
        <BannerSingle />
        <Pickup />
        <News />
        <Champion />
        <Sns />
        <Modal :isVisible="modalVisible" @close="closeModal" />
      </Layout>
    </template>
  </transition>
</template>

<style lang="scss">
body {
  font-size: 14px;
  font-family: "Hiragino Kaku Gothic Pro", sans-serif;

  &::before {
    display: none;
    content: '';
    background-color: red;
    position:absolute;
    left: 50%;
    width: 1px;
    height: 500px;
  }

  .loading {
    position: fixed;
    width: 100%;
    height: 100%;
    background: #fff;
    top: 0;
    left: 0;
    z-index: 999;
    transition: opacity 1s ease;

    img {
      width: 200px;
      height: auto;
      position: absolute;
      top: 50%;
      left: 50%;
      opacity: 0;
      transform-origin: center;
      transform: translate(-50%, -50%) scale(1.5);
      transition: all .4s ease-in-out;
    }

    &.active {
      img {
        opacity: 1;
        transform: translate(-50%, -50%) scale(1);
      }
    }

    &.fadeout {
      img {
        opacity: 0;
      }
    }
  }
}

.opacity-enter {
  opacity: 0;
}
.opacity-enter-active {
  transition: opacity 1s;
}
.opacity-enter-to {
  opacity: 1;
}
.opacity-leave {
  opacity: 1;
}
.opacity-leave-active {
  transition: opacity 1s;
}
.opacity-leave-to {
  opacity: 0;
}
</style>
