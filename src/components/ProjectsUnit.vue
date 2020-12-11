<template>
    <br><br>
    <div class='container'>
        <h3><i class='fas fa-star'></i> Personal Projects</h3>
    </div>
    <div id='projects-unit' class='container-fluid'>
        <div class='d-flex flex-md-row flex-column padded-row'>
            <div v-for='project in projects' :key='project.name' class='col'>
                <div class='card panel-bg shadow'>
                    <div class='row g-0'>
                        <div class='col-xl-3'>
                            <div class='icon-container'>
                                <img @load='handleImageLoad' :src='`assets/icons/${project.icon}`' class='icon-img rounded-circle' :style="{ 'border': 'solid 4px ' + project.icon_border_color }" />
                            </div>
                        </div>
                        <div class='col-xl-9'>
                            <div class='card-body'>
                                <h5 class='text-light'><b>{{project.name}}</b></h5>
                                <p>{{project.description}}</p>
                                <div v-if='project.link != ""'>
                                    <a class='btn btn-outline-light' target="_blank" :href='project.link'>
                                        Link <i class='fa fa-arrow-circle-o-right'></i>
                                    </a>
                                </div>
                                <div v-else>
                                    <button class='btn btn-dark transparent-1' data-toggle="tooltip" title="Link will become available when project is published" disabled>
                                        <i class='fa fa-cogs'></i> In Development
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import projectsData from '../json/projects.json';
    
    export default{
        data(){
            return{
                projects:projectsData.data,
                numImagesLoaded: 0
            }
        },
        computed:{
            numImagesToLoad: function(){
                return this.projects.length;
            }
        },
        emits: ['component-loaded'],
        methods: {
            //throw component loaded event after all images are loaded
            handleImageLoad: function(){
                this.numImagesLoaded++;
                if(this.numImagesLoaded == this.numImagesToLoad){
                    this.$emit('component-loaded');
                }
            }
        }
    }
</script>

<style>
    .padded-row{
        padding-left:3em;
        padding-right:3em;
        padding-top:1em;
    }
    .icon-container{
        padding-left:0.5em;
        filter:blur(0.4px);
    }
    .icon-img{
        width:100px;
        height:100px;
        margin-top:1em;
        margin-left:0.5em;
    }

    /* remove padded-row when in smaller device */
    @media screen and (max-width:755px){
        .padded-row{
            padding:0;
        }
    }
</style>