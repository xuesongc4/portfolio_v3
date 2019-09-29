<template>
    <div class="info-container" :class="{'show': sideShow !== ''}">
        <div id="info">
            <div :key="index" v-for="(info, index) in applications" class="app-info" :class="{'show': sideShow === index}">
                <h4>{{info.title}}</h4>
                <div class="info">
                    <p>
                        {{info.info}}
                    </p>
                    <div class="links">
                        <a target="_blank" :href="info.url">Live Site</a>
                        <a target="_blank" :href="info.gitUrl">GitHub</a>
                    </div>
                </div>
            </div>
        </div>
        <div class="close-out-container">
            <div @click="closeInfo" id="close-out">X</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CubeInfo",
        props: ['applications', 'side'],
        data(){
            return{
                sideShow: this.side,
            }
        },
        watch:{
            side: function (newSide){
                this.sideShow = newSide.data;
            }
        },
        methods:{
            closeInfo(){
                this.$emit("closeInfo",{data:'close'});
                this.sideShow = "";
            }
        }
    }
</script>

<style scoped>
    .show{
        display:block !important;
    }
    .info-container{
        position: absolute;
        right: 450px;
        top: 150px;
        display: none;
    }
    #info {
        border: white 5px solid;
        box-sizing: border-box;
        border-radius: 40px 0 40px 40px;
        background: rgba(255,255,255,.5);
        height: 460px;
        width: 400px;
        font-size: 20px;
    }
    .app-info{
        display:none;
    }
    .close-out-container{
        border: solid white 5px;
        border-radius: 50%;
        width: 60px;
        height: 60px;
        background: url('../assets/galaxy3.jpg')no-repeat center center fixed;
        position: absolute;
        top: -33px;
        right: -33px;
        display: inline-block;
        transition-duration: .5s;
    }
    #close-out{
        border-radius: 50%;
        width: 60px;
        height: 60px;
        text-align: center;
        line-height: 60px;
        color: white;
        font-weight: 700;
        font-size: 40px;
        transition-duration: .3s;
        background-color: rgba(0,0,0,.5);
        z-index: 10;
    }

    #close-out:hover{
        background-color: rgba(255,255,255,.5);
    }

    .close-out-container:hover{
        box-shadow: 0 0 20px 5px white;
        cursor: pointer;
    }

    #info .info_content{
        padding: 0 20px;
        margin-top: -70px;
    }
    .tracker-container .tracker{
        position: absolute;
        bottom: 20px;
        left: 21%;
        width: 220px;
    }

    .side1, .side2, .side3, .side4{
        display: none;
    }

    @media only screen and (max-width: 726px) {
        #info {
            background: rgba(255,255,255,.7);
            height: 500px;
            width: 315px;
            margin-top: -170px;
            right: 0;
            border-radius: 30px;
        }
        #info h4{
            font-size: 25px;
        }

        #close-out-container{
            right:-240px;
            top:-5px;
        }
    }
</style>