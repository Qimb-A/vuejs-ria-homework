<template>
  <div id="app" class="d-flex justify-content-center">
    <div class="w-75 p-3">
      <h2>Інформація про користувача</h2>
      <hr>
      <AddUser @submit='onSubmit'/>
      <hr>
      <p class="text-lg-left">Кількість користувачів: <b>{{maxUsers}}</b></p>
      <UserList
      v-bind:users="users" />
    </div>
  </div>
</template>

<script>
import AddUser from "@/components/AddUser";
import UserList from "@/components/UserList";
export default {
  name: 'App',
  components: {
    AddUser,
    UserList
  },
  data() {
    return {
      users: [],
      maxUsers: 0,
    }
  },
  methods:{
    onSubmit(data){
      this.users.push(Object.assign({id:this.maxUsers + 1}, data))
      ++this.maxUsers
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
