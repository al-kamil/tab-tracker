<template>
  <div>
    <h1>Register</h1>
    <input type="email" v-model="email" name="email" placeholder="email" />
    <input type="password" v-model="password" name="password" placeholder="password" />
    <br>
    <div class="error" v-html="error"></div>
    <button @click="register">Register</button>
  </div>
</template>

<script>
  import AuthenticationService from '@/services/AuthenticationService';
  export default {
    data() {
      return {
        email: 'kamilmatnoor@gmail.com',
        password: '123456',
        error: null
      };
    },
    // watch: {
    //   email(value) {
    //     console.log('Email has changed', value)
    //   }
    // },
    methods: {
      async register() {
        try {
          await AuthenticationService.register({
            email: this.email,
            password: this.password
          });
        } catch (error) {
          this.error = error.response.data.error
        }
  
      }
    }
    // mounted() {
    //   setTimeout(() => {
    //     this.email = "Hello World"
    //   }, 2000)
    // }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .error {
    color: red;
  }
</style>
