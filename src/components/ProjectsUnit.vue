<template>
    <br><br>
    <div id='projects-unit' class='container text-light'>
        <h3><i class='fas fa-star'></i> Personal Projects</h3>
        <div class='d-flex flex-md-row flex-column'>
            <div class='card panel-bg shadow' v-for='project in projects' :key='project.name'>
                <div class='card-body'>
                    <h4><b>{{project.name}}</b></h4>
                    <hr>
                    <p>{{project.description}}</p>
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
                projects:projectsData.data
            }
        }
    }
</script>