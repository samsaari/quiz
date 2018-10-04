<template>
  <div id="app">
    <img class="logo" alt="Vue logo" src="./assets/logo.png">
    <quiz />
  </div>
</template>

<script>
import quiz from './components/quiz.vue';

export default {
  name: 'app',
  components: {
    quiz,
  },
};
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logo {
  max-width: 120px;
}
</style>
