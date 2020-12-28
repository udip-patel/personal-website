<template>
  <div v-show='!isContentLoaded'>
    <div class='spinner'></div>
  </div>
  <transition name='smoothFadeIn'>
    <div class='main-content' v-show='isContentLoaded'>
      <HeroUnit :isLoaded="this.isContentLoaded" @component-loaded="this.onComponentLoaded" 
        name="Udip Patel" title="Software Developer" linkedinURL="https://www.linkedin.com/in/udippatel/" 
        githubURL="https://github.com/udip-patel" email="patel.udip@gmail.com">
      </HeroUnit>
      <ToolsUnit @component-loaded="this.onComponentLoaded"></ToolsUnit>
      <ProjectsUnit @component-loaded="this.onComponentLoaded"></ProjectsUnit>
      <br><br><br><br><br>
      <!-- footer will stick to bottom of page due to: mt-auto & flexbox style of main-content class !-->
      <div class='dynamic-backlit-bg mt-auto'>
        <footer class="py-4 flex-shrink-0 text-center">
          <img class='spanning-img' src='/assets/logos/logo-backdrop.png'>
        </footer>
      </div>
    </div>
  </transition>

</template>

<script>
import HeroUnit from './components/HeroUnit.vue'
import ToolsUnit from './components/ToolsUnit.vue'
import ProjectsUnit from './components/ProjectsUnit.vue'

export default {
  name: 'App',
  components: {
    HeroUnit, ToolsUnit, ProjectsUnit
  },
  data(){
    return{
      isContentLoaded: false,
      numComponentsToLoad: 3,
      numComponentsLoaded: 0,
    }
  },
  methods: {
    //display page content ONLY after all components are loaded
    onComponentLoaded() { 
      this.numComponentsLoaded++;
      if(this.numComponentsLoaded == this.numComponentsToLoad){
        this.isContentLoaded = true;
      }
    }
  }
}
</script>

<style>
/* make scrollbar transparent */
html {
  overflow:scroll;
}
::-webkit-scrollbar {
    width: 0px;
    background: transparent; 
}

body{
  margin:0px;
  background: #2e2e2e !important;
}

footer{
  height:100px;
}

#app {
  font-family: 'Nunito', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #c7c7c7;
}

.main-content{
  display:flex;
  min-height: 100vh;
  flex-direction:column;
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

.shadowed{
  box-shadow:0 6.4px 14.4px 0 rgba(255,255,255,0.132),0 1.2px 3.6px 0 rgba(255,255,255,0.108)!important
}

/* 'moving', blurred gradient background */
.dynamic-backlit-bg{
    background-repeat: no-repeat;
    background: linear-gradient(-45deg, #bcba62, #8d62bc, #3e92d8, #00F260);
    background-size: 400% 400%;
    animation: gradient 15s ease infinite;
    z-index: -1;
    filter:blur(27px);
}

.spanning-img{
  width: 100%;
  height:150px;
}

.smoothFadeIn-enter-active {
  animation: smoothFadeIn 2s;
}


/* animations */
@keyframes smoothFadeIn {
  0% { opacity: 0;  }
  100% { opacity: 1; }
}

@keyframes gradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
/* spinner */
@keyframes spinner {
  to {transform: rotate(360deg);}
}
 
.spinner:before {
  content: '';
  box-sizing: border-box;
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100px;
  height: 100px;
  margin-top: -10px;
  margin-left: -10px;
  border-radius: 50%;
  border: 10px solid transparent;
  border-top-color: #3e92d8;
  border-bottom-color: #3e92d8;
  animation: spinner .8s ease infinite;
}
 /* in small devices, spinner needs to be re-aligned to center */
 @media screen and (max-width:576px){
   .spinner:before{
     left:40%;
   }
 }
</style>
