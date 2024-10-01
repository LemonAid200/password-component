<template>
  <PasswordComponent/>
</template>

<script>
import PasswordComponent from './components/PasswordComponent.vue'

export default {
  name: 'App',
  components: {
    PasswordComponent
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@200..800&display=swap');


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  font-family: "Manrope", sans-serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
}
</style>
