<template>
  <nav>
    <h2>Home</h2>
    <router-link to="/" exact-active-class="link--active" class="link">Home</router-link>
    <router-link to="/users" exact-active-class="link--active" class="link">Users</router-link>
  </nav>
</template>

<style scoped>
  .link--active {
    font-size: 20px;
  }

  .link {
    margin-right: 10px;
  }
</style>
