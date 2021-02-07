<template>
  <div class="main">
    <button @click="show = !show">切り替え</button>
    <transition
      :css= "false"
       @before-enter="beforeEnter"
       @enter="enter"
       @leave="leave"
    >
      <div class="circle" v-if="show"></div>
    </transition>
    <transition
      enter-to-class=""
      enter-active-class="animate__animated animate__bounce"
      leave-active-class="animate__animated animate__shakeX"
      leave-to-class=""
      >
      <p v-if="show">hello</p>
    </transition>
    <transition name="slide">
      <p v-if ="show">bye</p>
    </transition>
    <component :is="mycComponent"></component>
  </div>
</template>

<script>
/* eslint-disable */
import A from './components/A';
import B from './components/B';

export default {
  components: {
    A,
    B
  },
  data() {
    return {
      show: true,
      mycComponent: 'A'
    };
  },
  methods: {
    beforeEnter(el) {
      el.style.transform ='scale(0)'
    },
    enter(el, done) {
      let scale = 0;
      const interval = setInterval(() => {
        el.style.transform = `scale(${scale})`;
        scale += 0.1;
        if (scale > 1) {
          clearInterval(interval);
          done();
        }
      }, 20);
    },
    leave(el, done) {
      let scale = 1;
      const interval = setInterval(() => {
        el.style.transform = `scale(${scale})`;
        scale -= 0.1;
        if (scale < 0) {
          clearInterval(interval);
          done();
        }
      }, 20);
    },
    leaveCancelled(el) {}
  }
}
/* eslint-enable */
</script>

<style scoped>
  .circle {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    background-color: pink;
    margin: auto;
  }

  .fade-enter {
    opacity: 0;
  }

  .fade-enter-active {
    transition: opacity .5s;
  }

  .fade-enter-to {
    opacity: 1;
  }

  .fade-leave {
    opacity: 1;
  }

  .fade-leave-active {
    transition: opacity .5s;
  }

  .fade-leave-to {
    opacity: 0;
  }

  .slide-enter,
  .slide-leave-to {
    opacity: 0;
  }

  .slide-enter-active {
    animation: slide-in 0.5s;
    transition: opacity 0.5s;
  }

  .slide-leave-active {
    animation: slide-in 0.5s reverse;
    transition: opacity 0.5s;
  }

  @keyframes slide-in {
    from {
      transform: translateX(100px);
    }
    to {
      transform: translateX(0);
    }
  }

  .main {
    width: 70%;
    margin: auto;
    padding-top: 5rem;
    text-align: center;
  }
</style>
