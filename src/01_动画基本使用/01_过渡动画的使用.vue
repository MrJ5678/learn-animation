<template>
  <div>
    <button @click="toggle">
      <span v-if="visible">显示</span>
      <span v-else>隐藏</span>
    </button>
    <transition name="fade">
      <h2 v-show="visible">hello !</h2>
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
  transition: opacity .3s ease;
}
</style>
