<template>
  <div class="container">
    <div>
      <button @click="toggle">
        <span v-if="visible">显示</span>
        <span v-else>隐藏</span>
      </button>
    </div>
    <transition name="fade" mode="out-in" :appear="true">
      <component :is="visible ? 'home' : 'about'"></component>
    </transition>
  </div>
</template>

<script>
import Home from './pages/Home.vue'
import About from './pages/About.vue'

export default {
  components: {
    Home,
    About
  },
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

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity .4s ease;
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
