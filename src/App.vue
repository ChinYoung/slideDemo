<template>
  <div id="app">
    <button @click="previous">previous</button>
    <button @click="next">next</button>
    <transition-group name="flip" class="flipWrapper">
      <div v-for="i in list" :key='i' v-show="i === current" class="item">{{i}}</div>
    </transition-group>
  </div>
</template>

<script>

export default {
  data() {
    return {
      list: [0, 1,2,3,4,5],
      current: 1
    }
  },
  methods: {
    previous() {
      this.current = (this.current - 1 + this.list.length) % this.list.length
    },
    next() {
      this.current = (this.current + 1) % this.list.length
    }
  }
}
</script>

<style>
.flipWrapper {
  position: absolute;
  width: 100%;
  top: 80px;
  left: 0;
  right: 0

}
.item {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  width: 100%;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ccc;
}
.flip-enter-active, .flip-leave-active {
  transition: all 1s;
}
.flip-enter{
  transform: translateX(-100%)
}
.flip-enter-to {
  transform: translateX(0)
}
.flip-leave {
  transform: translateX(0) translateY(-60px)
}
.flip-leave-to {
  transform: translateX(100%)
}
</style>
