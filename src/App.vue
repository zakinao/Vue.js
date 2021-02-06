<template>
  <div>
    <LikeHeader></LikeHeader>
    <h2>{{number}}</h2>
    <LikeNumber></LikeNumber>
    <LikeNumber :totalNumber='number'></LikeNumber>
  </div>
</template>

<script>
import LikeHeader from './components/LikeHeader.vue';

export default {
  data() {
    return {
      number: 0
      }
  },
  components: {
    LikeHeader
  }
}
</script>

<style scoped>
  div {
    border: 1px solid blue;
    }
</style>
