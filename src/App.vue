<template>
  <HeroUnit name="Udip Patel" title="Software Developer" linkedinURL="https://www.linkedin.com/in/udippatel/" githubURL="https://github.com/udip-patel" email="patel.udip@gmail.com"></HeroUnit>
</template>

<script>
import HeroUnit from './components/HeroUnit.vue'

export default {
  name: 'App',
  components: {
    HeroUnit
  }
}
</script>

<style>
body{
  margin:0px;
  background: black !important;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.transparent-1{
  opacity: 0.5;
}
</style>
