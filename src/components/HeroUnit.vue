<template>
  <div id="hero-unit">
    <div id="particles-bg" class='dynamic-backlit-bg'>
      <div class='sliding-img vertically-placed'></div>
    </div>
    <br />
    <div class="d-flex flex-column">
      <div class="row mx-auto">
        <div class="alert alert-info transparent-1 shadow text-center">
            <div id='typed-source-string'>
              <p>Hi there, ^500 I am <b>{{name}}</b>, ^250 a {{title}}.</p>
            </div>
            <h1 id='typed-content'></h1>
        </div>
      </div>
      <div class="row mx-auto">
        <img @load="handleImageLoad" src="/assets/profile.jpg" class="row profile-img img-thumbnail rounded-circle mx-auto" />
      </div>
      <br />
      <div class="row mx-auto">
        <div class="btn-group shadow" role="group">
          <a class="btn btn-light" :href=linkedinURL target="_blank" data-toggle="tooltip" title="LinkedIn">
            <b><i class="fab fa-linkedin"></i></b>
          </a>
          <a class="btn btn-dark" :href=githubURL target="_blank" data-toggle="tooltip" title="Github">
            <b><i class="fab fa-github"></i></b>
          </a>
          <a class="btn btn-light" :href="`mailto:${email}`" data-toggle="tooltip" title="Send me an email">
            <b><i class="fas fa-envelope"></i></b>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import "particles.js";
  import Typed from 'typed.js'

  export default {
    props: ["isLoaded", "name", "title", "linkedinURL", "githubURL", "email"],
    emits: ['component-loaded'],
    watch: {
      // when this component is loaded, it will be displayed, so start any animations
      isLoaded: function(){
        this.startAnimationsOnDisplay();
      }
    },
    methods: {
      //throw component loaded event after all content is loaded
      handleImageLoad: function(){
        this.$emit('component-loaded');
      },
      //trigger particles js library to display, once particles displayed, call typed.js function
      loadParticlesJS: function(){
        window.particlesJS.load(
          "particles-bg",
          "/assets/particles-data.json",
          this.renderTypedJSText 
        );   
      },
      //trigger typed.js text to display
      renderTypedJSText: function(){
        new Typed('#typed-content', {
          stringsElement: '#typed-source-string',
          showCursor: false,
          typeSpeed: 30,
        });
      },
      //start rendering special animations
      startAnimationsOnDisplay: function(){
        this.loadParticlesJS();  
      }
    }
  };
</script>

<style>
  #hero-unit, #particles-bg {
    width: 100%;
    height: 24em;
  }

  #typed-source-string{
    display:none !important;
  }

  #particles-bg {
    position: absolute;
    overflow: hidden;
  }

  .profile-img{
    width:185px;
    opacity:0.95;
  }

  .vertically-placed{
    position: absolute;
    top: 60%;
  }

  .sliding-img{
    background: url('/assets/logos/long-logo-wave-backdrop.png') repeat-x;
    animation: slide 45s linear infinite;
    height:150px;
    width: 9258px;
  }


  @keyframes slide{
    0%{
      transform: translate3d(0, 0, 0);
    }
    100%{
      transform: translate3d(-3086px, 0, 0);
    }
  }

  /* display rules for responsive design of hero unit */
  @media screen and (max-width:755px){
    #hero-unit, #particles-bg{
      height:27em !important
    }
  }

  @media screen and (max-width:450px){
    #hero-unit, #particles-bg{
      height:32em !important
    }
  }
</style>
