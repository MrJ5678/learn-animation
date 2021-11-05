<template>
  <div class="container">
    <div>
      <button @click="toggle">
        <span v-if="visible">显示</span>
        <span v-else>隐藏</span>
      </button>
    </div>
    <transition @enter="enter" @leave="leave" :css="false">
      <h2 style="display: inline-block" v-if="visible">hello</h2>
    </transition>
  </div>
</template>

<script>
import gsap from 'gsap'

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
    // beforeEnter() {
    //   console.log('before enter')
    // },
    enter(el, done) {
      console.log('enter')
      gsap.from(el, {
        scale: 0,
        x: 200,
        onComplete: done
      })
    },
    // afterEnter() {
    //   console.log('after leave')
    // },
    // beforeLeave() {
    //   console.log('before leave')
    // },
    leave(el, done) {
      console.log('leave')
      gsap.to(el, {
        scale: 0,
        x: 200,
        onComplete: done
      })
    },
    // afterLeave() {
    //   console.log('after leave')
    // }
  },
}
</script>

<style scoped>

</style>
