<template>
  <SignupForm />
  <Footer/>
</template>

<script>
import SignupForm from "./components/SignupForm.vue"
import Footer from "./components/Footer.vue"
export default {
  name: 'App',
  components: {SignupForm, Footer}
}
</script>

<style>
body{
  background: #2c3e50;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
