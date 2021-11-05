<template>
  <div>
    <input type="text" v-model="keyword" />
    <transition-group
      tag="ul"
      name="fade"
      :css="false"
      @before-enter="beforeEnter"
      @enter="enter"
      @leave="leave"
    >
      <li v-for="(item, index) in filteredNames" :key="item" :data-index="index">
        {{ item }}
      </li>
    </transition-group>
  </div>
</template>

<script>
import gsap from "gsap"

export default {
  data() {
    return {
      names: ["abc", "cba", "nba", "jld"],
      keyword: "",
    }
  },
  computed: {
    filteredNames() {
      return this.names.filter(name => name.indexOf(this.keyword) !== -1)
    },
  },
  methods: {
    beforeEnter(el) {
      el.style.opacity = 0
      el.style.height = 0
    },
    enter(el, done) {
      gsap.to(el, {
        opacity: 1,
        height: "1.5em",
        delay: el.dataset.index * 0.3,
        onComplete: done,
      })
    },
    leave(el, done) {
      gsap.to(el, {
        opacity: 0,
        height: 0,
        delay: el.dataset.index * 0.3,
        onComplete: done,
      })
    },
  },
}
</script>

<style scoped></style>
