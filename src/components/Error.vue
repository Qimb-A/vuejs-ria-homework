<template>
<div>
    <div v-if="Age" class="alert alert-danger" role="alert">
    Age is wrong, must be less then 3 digits.
  </div>
      <div v-if="Email" class="alert alert-danger" role="alert">
    Email is incorrect.
  </div>
        <div v-if="Name" class="alert alert-danger" role="alert">
    Name is to long, max length = 20.
  </div>
</div>
</template>

<script>
export default {
  name: "Error",
  props: ['Age','Email','Name']
}
</script>

<style scoped>

</style>