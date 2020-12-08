<template>
  <HeroUnit name="Udip Patel" title="Software Developer" linkedinURL="https://www.linkedin.com/in/udippatel/" githubURL="https://github.com/udip-patel" email="patel.udip@gmail.com"></HeroUnit>
  <ToolsUnit></ToolsUnit>
  <ProjectsUnit></ProjectsUnit>
  <FooterUnit></FooterUnit>
</template>

<script>
import HeroUnit from './components/HeroUnit.vue'
import ToolsUnit from './components/ToolsUnit.vue'
import ProjectsUnit from './components/ProjectsUnit.vue'
import FooterUnit from './components/FooterUnit.vue'

export default {
  name: 'App',
  components: {
    HeroUnit, ToolsUnit, ProjectsUnit, FooterUnit
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
  border: solid 0.25px #454545 !important;
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
