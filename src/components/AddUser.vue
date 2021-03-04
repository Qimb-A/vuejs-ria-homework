<template>
  <div>
    <Error v-if="this.formName.length > 20" v-bind:Name="this.formName.length > 20" />
    <Error v-if="isEmailError && this.formEmail != ''" v-bind:email="isEmailError && this.formEmail != ''"/> 
    <Error v-if="this.formAge.length > 3 " v-bind:Age="this.formAge.length > 3 "/>
    <form>
      <div class="row g-3">
        <div class="col-sm-5">
          <input v-model="formName" type="text" class="form-control" placeholder="Your Name">
        </div>
        <div class="col-sm-5">
          <input v-model="formEmail" type="email" @blur="isEmailTouched = true" :class="{ error: isEmailError }" class="form-control" placeholder="Your Email">
        </div>
        <div class="col-sm">
          <input v-model="formAge" type="text" class="form-control" @keypress="onlyNumber($event)" placeholder="Your Age" >
        </div>
      </div>
      <br>
      <div class="col">
        <button @click.prevent='submit' :disabled="!isEmailValid || this.formName.length > 20 ||this.formName == ''||this.formEmail == ''|| this.formAge == ''||this.formAge.length > 3" type="submit" class="btn btn-primary">Add User</button>
      </div>

    </form>
  </div>

</template>

<script>
const emailCheckRegex = /^(([^<>()\[\]\.,;:\s@\"]+(\.[^<>()\[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;

import Error from "@/components/Error";
export default {
  name: "AddUser",
  components: {Error},
  data(){
    return{
    formName: '',
    formEmail: '',
    formAge: '',
      email: null,
      isEmailTouched: false,
    }
  },
computed: {
    isEmailValid() {
      return emailCheckRegex.test(this.formEmail);
    },
    isEmailError() {
      return !this.isEmailValid && this.isEmailTouched;

    },
  },

  methods:{
    submit(){
      if (!this.isEmailValid) {
        return;

      }
         this.$emit('submit', {
      name: this.formName,
      email: this.formEmail,
      age: this.formAge
    })
    },
    onlyNumber($event) {
   let keyCode = ($event.keyCode ? $event.keyCode : $event.which);
   if ((keyCode < 48 || keyCode > 57) && keyCode !== 46) {
      $event.preventDefault();
   }
}
    
  }
}
</script>

<style scoped>

</style>