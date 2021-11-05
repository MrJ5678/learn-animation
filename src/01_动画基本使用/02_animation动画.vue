<template>
  <div class="container">
    <div>
      <button @click="toggle">
        <span v-if="visible">显示</span>
        <span v-else>隐藏</span>
      </button>
    </div>
    <transition name="fade">
      <div style="display: inline-block" v-show="visible">hello !</div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      visible: true,
    }
  },
  methods: {
    toggle() {
      this.visible = !this.visible
    },
  },
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.fade-enter-active {
  animation: bounce 0.4s ease;
}

.fade-leave-active {
  animation: bounce 0.4s reverse;
}

@keyframes bounce {
  0% {
    transform: scale(0);
  }

  50% {
    transform: scale(1.2);
  }

  100% {
    transform: scale(1);
  }
}
</style>
