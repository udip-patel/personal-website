<template>
  <HeroUnit name="Udip Patel" title="Software Developer" linkedinURL="https://www.linkedin.com/in/udippatel/" githubURL="https://github.com/udip-patel" email="patel.udip@gmail.com"></HeroUnit>
  <ToolsUnit></ToolsUnit>
</template>

<script>
import HeroUnit from './components/HeroUnit.vue'
import ToolsUnit from './components/ToolsUnit.vue'

export default {
  name: 'App',
  components: {
    HeroUnit, ToolsUnit
  }
}
</script>

<style>
body{
  margin:0px;
  background: #242424 !important;
}

.panel-bg{
  background: #171717 !important;
  border: solid 0.25px #454545;
}

#app {
  font-family: 'Nunito', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.transparent-1{
  opacity: 0.5;
}
</style>
