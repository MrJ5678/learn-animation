<template>
  <div>
    <button @click="addNum">添加数字</button>
    <button @click="removeNum">删除数字</button>
    <transition-group tag="p" name="fade">
      <span v-for="item in numbers" :key="item" class="item">
        {{ item }}
      </span>
    </transition-group>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      numberCounter: 10,
    }
  },
  methods: {
    addNum() {
      this.numbers.splice(this.getRandomIndex(), 0, this.numberCounter++)
    },
    removeNum() {
      this.numbers.splice(this.getRandomIndex(), 1)
    },
    getRandomIndex() {
      return Math.floor(Math.random() * this.numbers.length)
    },
  },
}
</script>

<style scoped>
.item {
  margin-right: 10px;
  display: inline-block;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}

.fade-leave-active {
  position: absolute;
}

.fade-move {
  transition: transform 1s ease;
}
</style>
