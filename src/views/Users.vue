<template>
  <div>
    <h3>Users</h3>
    <router-link to="/users/1">ユーザー1</router-link>
    <router-link to="/users/2">ゆーざー2</router-link>
    <hr>
    <h1>User No. {{ id }}</h1>
    <router-link :to="{name: 'users-id-profile', params: {id: Number(id) + 1} }">次のユーザー</router-link>
    <router-view></router-view>
    <div style="height: 700px;"></div>
  </div>
</template>

<script>
export default {
  props: ["id"]
}
</script>
