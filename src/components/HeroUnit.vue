<template>
  <div id="hero-unit">
    <div id="particles-bg" class='dynamic-backlit-bg'>
      <img class='spanning-img vertically-centered' src='/assets/logos/logo-backdrop.png'>
    </div>
    <br />
    <div class="d-flex flex-column">
      <div class="row mx-auto">
        <div class="alert alert-info transparent-1 shadow">
            <div id='typed-source-string'>
              <p>Hi there, ^500 I am <b>{{name}}</b>, ^250 a {{title}}.</p>
            </div>
            <h1 id='typed-content'></h1>
        </div>
      </div>
      <div class="row mx-auto">
        <img @load="handleImageLoad" src="/assets/profile.png" class="row profile-img img-thumbnail rounded-circle mx-auto" />
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

  #particles-bg {
    position: absolute;
  }

  #typed-source-string{
    display:none !important;
  }
  .profile-img{
    width:185px;
    opacity:0.95;
  }

  .vertically-centered{
    position: absolute;
    top: 40%;
  }

  /* display rules for responsive design of hero unit */
  @media screen and (max-width:755px){
    #hero-unit, #particles-bg{
      height:27em !important
    }
  }

  @media screen and (max-width:450px){
    #hero-unit, #particles-bg{
      height:31em !important
    }
  }
</style>
