<template>
  <div>
    <HeaderComp/>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import "bootstrap"

export default {
  name: 'App',
  components: {
    HeaderComp
  }
}
</script>

<style lang="scss">

@import "bootstrap/dist/css/bootstrap.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

html{
  max-width: 1440px;
  margin: 0 auto;
}

body{
  background-color: #1E2D3B;
}

</style>
