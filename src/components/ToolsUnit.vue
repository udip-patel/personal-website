<template>
    <br><br>
    <div id='tools-unit' class='container'>
        <h3><i class='fas fa-toolbox'></i> Tools and Frameworks</h3>
        <div class='row mx-auto panel-bg shadow'>
            <img class='tool-img' v-for='tool in tools' :key='tool.name' :src='`assets/logos/${tool.image}`' data-toggle='tooltip' data-placement='bottom' :title='tool.name' />
        </div>
    </div>
</template>

<script>
    import toolsData from '../json/toolsAndFrameworks.json';

    export default{
        data(){
            return{
                tools: toolsData.data
            }
        }
    }
</script>

<style>
    .tool-img{
        width: 90px;
        height: 90px;
        padding:15px;
    }
</style>