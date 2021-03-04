<template>
  <table class="table">
    <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Age</th>
    </tr>
    </thead>
    <tbody v-for="item of users">
    <tr>
      <th scope="row">{{item.id}}</th>
      <td>{{item.name | capitalize}}</td>
      <td>{{item.email}}</td>
      <td>{{item.age}}</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
name: "UserList",
  filters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
},
props:['users']
}
</script>

<style scoped>

</style>