<template>
  <div>
    <LikeHeader>
      <h2>こんにちは</h2>
    </LikeHeader>
    <LikeNumber :totalNumber='number' @my-click='incrementNumber'></LikeNumber>
    <button @click="currentComponent= 'Home'">Home</button>
    <button @click="currentComponent= 'About'">About</button>
    <keep-alive>
      <component :is="currentComponent"></component>
    </keep-alive>
    <div>
      <hr>
      <h2>イベントのフォーム</h2>
      <EventTitle v-model="eventData.title"></EventTitle>
    </div>
  </div>
</template>

<script>
import LikeHeader from './components/LikeHeader.vue';
import About from './components/About';
import Home from './components/Home';
import EventTitle from './components/EventTitle.vue';

export default {
  data() {
    return {
      number: 0,
      currentComponent: 'Home',
      eventData: {
        title:''
      }
      }
  },
  components: {
    LikeHeader,
    About,
    Home,
    EventTitle
  },
  methods: {
    incrementNumber(value) {
      this.number = value
    }
  }
}
</script>
