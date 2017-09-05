<template>
  <div>
    <!-- 过渡/动画 -->
     <button v-on:click="show = !show">
      ToggleShow
    </button>
    <button v-on:click="toggleCom">
      ToggleCom
    </button>
    <button v-on:click="show = !show">
      ToggleJs
    </button>
    <div class="ab">
      <!-- css过渡 -->
      <!-- <transition name="fade">
        <p v-show="show">i am show</p>
      </transition> -->
      <!-- <transition name="my-trans" mode="out-in"> -->
        <!-- <p v-show="show">i am show</p> -->
        <!-- <p v-if="show">i am show</p> -->
        <!-- 动态组件 -->
         <!-- <div :is="currentView"></div> -->
        <!-- 多元素过渡 标签相同需要指定key-->
        <!-- <p v-if="show" key="1">i am show</p> -->
        <!-- <div v-else>not in show</div> -->
        <!-- <p v-else key="2">not in show</p> -->
      <!-- </transition> -->
      <!-- JS过渡 -->
      <transition
      v-on:before-enter="beforeEnter"
      v-on:enter="enter"
      v-on:leave="leave"
      v-bind:css="false">
        <p class="animate-p" v-show="show">i am show</p>

      </transition>
    </div>
  </div>
</template>

<script>
// import Vue from 'vue'
import ComA from './components/A'
import ComB from './components/B'
import $ from 'jquery'

export default {
  components: {
    ComA, ComB
  },
  data () {
    return {
      show: true,
      currentView: 'com-a'
    }
  },
  methods: {
    beforeEnter: function (el) {
      $(el).css({
        left: '-500px',
        opacity: 0
      })
    },
    enter: function (el, done) {
      $(el).animate({
        left: 0,
        opacity: 1
      }, {
        duration: 1500,
        complete: done
      })
    },
    leave: function (el, done) {
      $(el).animate({
        left: '500px',
        opacity: 0
      }, {
        duration: 1500,
        complete: done
      })
    },
    toggleCom () {
      if (this.currentView === 'com-a') {
        this.currentView = 'com-b'
      } else {
        this.currentView = 'com-a'
      }
    }
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
.ab {
  position: absolute;
  left: 150px;
  top: 300px;
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
.my-trans-leave-to {
  transform: translateY(500px);
  opacity: 0;
}
.animate-p {
  position: absolute;
  top: 0;
  left: 0;
}
</style>
