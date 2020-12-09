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
#app {
  font-family: 'Nunito', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #c7c7c7;
}

body{
  margin:0px;
  background: #2e2e2e !important;
}

.transparent-1{
  opacity: 0.5;
}

/*basic card display attributes */
.panel-bg{
  background: #171717 !important;
  border: solid 0.25px #454545 !important;
  border-radius:5px !important;
}

/* 'moving', blurred gradient background */
.dynamic-backlit-bg{
    background-repeat: no-repeat;
    background: linear-gradient(-45deg, #c44d58, #8d62bc, #3e92d8, #9aebdb);
    background-size: 400% 400%;
    animation: gradient 15s ease infinite;
    z-index: -1;
}

/* animation for background */
@keyframes gradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
</style>
