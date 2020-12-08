<template>
  <div id="hero-unit">
    <div id="particles-bg" class='dynamic-backlit-bg'></div>
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
        <img src="https://via.placeholder.com/170" class="row img-thumbnail rounded-circle mx-auto" />
      </div>
      <br />
      <div class="row mx-auto">
        <div class="btn-group shadow" role="group">
          <a class="btn btn-light" :href=linkedinURL target="_blank" data-toggle="tooltip" title="LinkedIn">
            <b><i class="fab fa-linkedin"></i></b>
          </a>
          <a class="btn btn-light" :href=githubURL target="_blank" data-toggle="tooltip" title="Github">
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
    props: ["name", "title", "linkedinURL", "githubURL", "email"],
    created: function() {
      window.particlesJS.load(
        "particles-bg",
        "/assets/particles-data.json",
        null        
      );      
    },
    mounted: function(){
      new Typed('#typed-content', {
        stringsElement: '#typed-source-string',
        showCursor: false,
        typeSpeed: 30,
      });
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
    filter: blur(1.5px);
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
