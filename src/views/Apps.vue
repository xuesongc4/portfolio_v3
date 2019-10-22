<template>
    <section id="applications">
        <Cube :applications="applications" :close="close" :side="cubeSide"  @selectSide="selectSide($event)"/>
        <CubeInfo :applications="applications" :side="infoSide"  @closeInfo="closeInfo($event)" @changeSide="changeSide($event)"/>
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
                infoSide:"",
                cubeSide:"",
                close:""
            }
        },
        props: ['applications'],
        methods: {
            selectSide($event){
                this.infoSide = $event;
            },
            closeInfo($event){
                this.close = $event;
            },
            changeSide($event){
                this.cubeSide = $event;
            }
        }
    }
</script>

<style scoped>
    #applications {
        background: url('../assets/images/galaxy3.jpg') no-repeat bottom center fixed;
        background-size: cover;
        position: relative;
    }

    .caption {
        position: absolute;
        color: white;
        bottom: 30%;
        left: 5%;
    }

    @media all and (min-width: 1024px) {
        .caption {
            bottom: 100px;
            left: 15%;
        }
    }


</style>