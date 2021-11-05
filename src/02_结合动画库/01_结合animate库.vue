<template>
  <div class="container">
    <div>
      <button @click="toggle">
        <span v-if="visible">显示</span>
        <span v-else>隐藏</span>
      </button>
    </div>
    <transition enter-active-class="animate__animated animate__bounceInUp" leave-active-class="animate__animated animate__bounceOutDown">
      <h2 style="display: inline-block" v-if="visible">hello</h2>
    </transition>
  </div>
</template>

<script>
export default {
  components: {},
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

</style>
