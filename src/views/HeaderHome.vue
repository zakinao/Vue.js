<template>
  <nav>
    <h2>Home</h2>
    <router-link to="/" exact-active-class="link--active" class="link">Home</router-link>
    <router-link to="/users" exact-active-class="link--active" class="link">Users</router-link>
    <button @click="increment(2)">+1</button>
    <button @click="decrement(2)">-1</button>
  </nav>
</template>

<script>

export default {
  methods: {
    increment() {
      this.$store.dispatch('count/increment', 2);
    },
    decrement() {
      this.$store.dispatch('count/decrement', 2);
    }
  }
};
</script>

<style scoped>
  .link--active {
    font-size: 20px;
  }

  .link {
    margin-right: 10px;
  }
</style>
