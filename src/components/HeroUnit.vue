<template>
  <div id="hero-unit">
    <div id="particles-bg"></div>
    <br />
    <div class="d-flex flex-column">
      <div class="row mx-auto">
        <div class="alert alert-info transparent-1 shadow">
          <h1>Hi there, I am <b>{{name}}</b>, a {{title}}</h1>
        </div>
      </div>
      <div class="row mx-auto">
        <img
          src="https://via.placeholder.com/170"
          class="row img-thumbnail rounded-circle mx-auto"
        />
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

  export default {
    name: "HeroUnit",
    props: ["name", "title", "linkedinURL", "githubURL", "email"],
    created: function() {
      window.particlesJS.load(
        "particles-bg",
        "/assets/particles-data.json",
        null
      );
    },
  };
</script>

<style>
  #hero-unit {
    /* size of hero unit */
    width: 100%;
    height: 24em;
    @media (max-width: 755px) {
      height: 27em !important;
    }
    @media (max-width: 450px) {
      height: 29em !important;
    }
  }

  #particles-bg {
    position: absolute;
    background-repeat: no-repeat;
    background: linear-gradient(-45deg, #c44d58, #8d62bc, #3e92d8, #9aebdb);
    background-size: 400% 400%;
    animation: gradient 15s ease infinite;

    filter: blur(1.5px);
    z-index: -1;

    /* size of particles background */
    width: 100%;
    height: 23em;
    @media (max-width: 755px) {
      height: 26em !important;
    }
    @media (max-width: 450px) {
      height: 30em !important;
    }
  }

  @keyframes gradient {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }
</style>
