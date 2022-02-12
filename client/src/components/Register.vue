<template>
  <div>
    <h1>Register</h1>
    <input type="email" name="email" v-model="email" placeholder="email"/>
    <br/>
    <input type="password" name="password" v-model="password" placeholder="password"/>
    <br/>
    <button @click="register">Register</button>
  </div>
</template>

<script>
import AuthService from '@/services/AuthService'
export default {
  data () {
    return {
      email: "m@v.com",
      password: "123456"
    }
  },
  watch: {
    email (value) {
      console.log("Email has changed", value)
    },
    password (value) {
      console.log("Password has changed", value)
    }
  },
  mounted () {
    setTimeout(() => {
      this.email = "test@x.com"
    }, 2000)
  },
  methods: {
    async register() {
      const response = await AuthService.register({
        email: this.email,
        password: this.password
      })
      console.log(response.data)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
