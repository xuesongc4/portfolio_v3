<template>
    <section id="applications">
        <Cube :applications="applications" :close="close"  v-on:selectSide="selectSide($event)"/>
        <CubeInfo :applications="applications" :side="side"  v-on:closeInfo="closeInfo($event)"/>
        <h3 class="caption">Click on a video for more info...</h3>
    </section>
</template>

<script>
    import Cube from '../components/Cube'
    import CubeInfo from "../components/CubeInfo";

    export default {
        name: "Apps",
        components: {
            CubeInfo,
            Cube
        },
        data(){
            return{
                side:"",
                close:""
            }
        },
        props: ['applications'],
        methods: {
            selectSide($event){
                this.side = $event;
            },
            closeInfo($event){
                this.close = $event;
            }
        }
    }
</script>

<style scoped>
    #applications {
        background: url('../assets/galaxy3.jpg') no-repeat bottom center fixed;
        background-size: cover;
        position: relative;
    }

    .caption {
        position: absolute;
        bottom: 100px;
        left: 15%;
        color: white;
    }
</style>