<template>
  <h1>Sign Up Now!</h1>
  <SignUpForm />
</template>

<script>
import SignUpForm from './components/SignUpForm.vue';
export default {
  name: 'App',
  components: { SignUpForm },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #064635;
  margin-top: 60px;
}
</style>
