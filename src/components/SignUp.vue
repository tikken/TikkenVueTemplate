<template>
<div>
  <h1>Sign Up</h1>
  <form class="sign-up">
    <input type="text" v-model="email" placeholder="email" autocomplete="on"><br/>
    <input type="password" v-model="password" placeholder="password" autocomplete="on"><br/>
    <input type="submit" @click="signUp" value="Sign Up" class="button">
  </form>
</div>
</template>

<script>
export default {
data() {
  return {
    email: '',
    password: ''
  }
 },
//Show loading process
computed: {
  loading() {
    return this.$store.getters.loading
  }
},
methods: {
  signUp() {
    const user = {
      email: this.email,
      password: this.password
    }
    this.$store.dispatch('registerUser', user)
    .then(() => {
      this.$router.push('/')
    })
    .catch(err => {})
  }
 }
}
</script>
<style lang="scss">
.sign-up {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
 & input {
    background: transparent;
    width: 15rem;
    padding: 15px;
    box-sizing: border-box;
    border: 1px solid #2c3e50;
    margin-bottom: 1rem;
    border-radius: 0;
  }
}
.button {
    text-decoration: none;
    color: #2c3e50;
    box-sizing: border-box;
    border: 1px solid #2c3e50;
    max-width: 5rem;
    text-transform: uppercase;
}
.errors {
    list-style: none;
    color: #e0115f;

    & li {
        margin-right: 2rem;
    }
}
.errors {
    list-style: none;
    color: #e0115f;

    & li {
        margin-right: 2rem;
    }
}
</style>
