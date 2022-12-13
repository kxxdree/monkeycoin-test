<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Register from './views/Register.vue'
import MainLogIn from './views/MainLogIn.vue'
import SignInVue from './views/SignIn.vue';

export default {
  components: { Register, MainLogIn, SignInVue},

}
</script>

<style>
* {
  font-family: 'Comic Neue', sans-serif;
  font-family: 'Manrope', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #0D1017;
}

/* @media screen and (max-width: 1920px) {
  html {
    font-size: 100%;
  }
}
@media screen and (max-width: 1770px) {
  html {
    font-size: 100%;
  }
}
@media screen and (max-width: 855px) {
  html {
    font-size: 90%;
  }
}
@media screen and (max-width: 540px) {
  html {
    font-size: 60%;
  }
} */
</style>