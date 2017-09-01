<template>
  <div>
    <!-- 过渡/动画 -->
    <button v-on:click="show = !show">
      Toggle
    </button>
    <div class="ab">
      <!-- <transition name="fade">
        <p v-show="show">i am show</p>
      </transition> -->
      <transition name="my-trans">
        <p v-show="show">i am show</p>
      </transition>
    </div>
  </div>
</template>

<script>
// import Vue from 'vue'
import ComA from './components/A'
export default {
  components: {
    ComA
  },
  data () {
    return {
      show: true
    }
  },
  methods: {

  }
}
</script>

<style>
html {
  height: 100%;
}
body {
  display: flex;
}
.fade-enter-active, .fade-leave-active {
  transition: all .5s ease-out;
}
.fade-enter, .fade-leave-to /* .fade-leave-active in below version 2.1.8 */ {
  opacity: 0;
}
.my-trans-enter-active, .my-trans-leave-active {
  transition: all .5s ease-out;
}
.my-trans-enter {
  transform: translateY(-500px);
  opacity: 0;
}
.my-trans-leave {
  transform: translateY(500px);
  opacity: 0;
}
</style>
