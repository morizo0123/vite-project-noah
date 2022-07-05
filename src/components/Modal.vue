<script lang="ts">
import { defineComponent, onMounted } from "vue"

export default defineComponent({
  props: {
    isVisible: Boolean
  },

  emits: ['close'],
  
  setup(props, { emit }) {

    onMounted(() => {
      console.log(props)
    })

    const onClose = () => {
      emit('close')
    }

    return {
      onClose
    }
  }
})
</script>

<template>
  <teleport to="body">
    <div class="modal" v-show="isVisible" @click="onClose"></div>
    <div class="modal-content" v-show="isVisible">
      <img src="/assets/logo_noah.svg" alt="">
      <p class="modal-content__text">このサイトは勉強用に作られたサイトです。</p>
    </div>
  </teleport>
</template>

<style scoped lang='scss'>
.modal {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: rgba(0,0,0,.5);
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 999998;
}

.modal-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgba(0,0,0,.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  
  background-color: white;
  width: 600px;
  height: auto;
  border-radius: 10px;
  padding: 40px 0;
  z-index: 999999;

  img {
    width: 200px;
    height: auto;
    margin-bottom: 24px;
  }

  &__text {
    font-weight: bold;
  }
}
</style>