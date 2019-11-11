<template>
    <div class="cube-container" :class="{'moveCube' : moveCubeData === 'move'}">
        <h2 class="page-title">Applications</h2>
        <div id="cube" :class="[rotateCubeData, cubeSideSelectedData]">
            <div class="cube-side cube-border"
                 :class="[{ 'front': index === 0 }, { 'right': index === 1 }, { 'back': index === 2 }, { 'left': index === 3 }, {'highlight':index === selected}]"
                 :key="index" v-for="(app, index) in applications" @click="cubeSelect(index); selected=index">
                <div class="cube-font">
                    {{app.title}}
                </div>
                <div class="video-container">
                    <video class="cube_video" autoplay loop muted>
                        <source v-if="app.videoUrl" :src="app.videoUrl" type="video/mp4">
                    </video>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Cube",
        props: ["applications", "close", "side"],
        data: function () {
            return {
                selected: "",
                rotateCubeData: "rotate",
                moveCubeData: "close",
                cubeSideSelectedData: ""
            }
        },
        watch:{
            close: function ($event){
                this.moveCubeData = $event.data;
                this.cubeDeSelect();
            },
            side: function ($event){
                this.selected = $event;
                this.cubeSelect($event);
            }
        },
        methods: {
            cubeSelect(side) {
                this.rotateCubeData = "";
                this.moveCubeData = "move";
                this.$emit('selectSide',{data:side});

                if (side === 0) {
                    this.cubeSideSelectedData = "show-front";
                } else if (side === 1) {
                    this.cubeSideSelectedData = "show-right";
                } else if (side === 2) {
                    this.cubeSideSelectedData = "show-back";
                } else if (side === 3) {
                    this.cubeSideSelectedData = "show-left";
                }
            },
            cubeDeSelect() {
                this.selected = "";
                setTimeout(() => {
                    this.moveCubeData = "";
                    setTimeout(() => {
                        this.rotateCubeData = "rotate";
                    }, 100)
                }, 500)
            }

        }
    }
</script>

<style scoped>

    .page-title {
        top: -180px;
        left: 50%;
        transform: translateX(-50%);
        color: white;
        position: absolute;
    }

    .moveCube {
        transform: translateX(-500px) !important;
    }

    .cube-container {
        width: 220px;
        height: 220px;
        -webkit-perspective: 1000px;
        perspective: 1000px;
        display: block;
        margin: auto;
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        top: 230px;
        transition-duration: .5s;
    }

    #cube {
        transform-style: preserve-3d;
    }

    #cube .cube-side {
        margin: 0;
        position: absolute;
        font-size: 20px;
        line-height: 40px;
    }

    #cube .front {
        transform: rotateY(0deg) translateZ(220px);
        color: #55ACEE;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }

    #cube .back {
        transform: rotateY(180deg) translateZ(220px);
        color: #FB9F19;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }

    #cube .right {
        transform: rotateY(90deg) translateZ(220px);
        color: #55ACEE;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }

    #cube .left {
        transform: rotateY(-90deg) translateZ(220px);
        color: red;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }


    .front:hover, .right:hover, .left:hover, .back:hover {
        cursor: pointer;
    }

    #cube {
        transition: transform 1s;
    }

    .show-front {
        transform: rotateY(15deg);
    }

    .show-back {
        transform: rotateY(-165deg);
    }

    .show-right {
        transform: rotateY(-75deg);
    }

    .show-left {
        transform: rotateY(-255deg);
    }

    .cube-video {
        width: 153%;
        margin-top: -35px;
        margin-left: -60px;
    }

    .video-container {
        width: 100%;
        height: 220px;
        overflow: hidden;
        position: relative;
    }

    video {
        position: absolute;
        width: 180%;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .cube-border {
        text-align: center;
        overflow: hidden;
        background-color: rgba(0, 0, 0, .6);
        border: 2px solid white;
        border-radius: 10px;
    }

    .rotate {
        animation-name: rotate-cube;
        animation-duration: 1400s;
        animation-iteration-count: infinite;
        animation-timing-function: linear;
    }

    .highlight {
        box-shadow: 0 0 80px 15px white;
        cursor: auto;
        pointer-events: none;
    }

    .cube-side.front.highlight {
        transform: rotateY(0deg) translateZ(400px) !important;
        transition-delay: .5s;
    }

    .cube-side.right.highlight {
        transform: rotateY(90deg) translateZ(400px) !important;
        transition-delay: .5s;
    }

    .cube-side.back.highlight {
        transform: rotateY(180deg) translateZ(400px) !important;
        transition-delay: .5s;
    }

    .cube-side.left.highlight {
        transform: rotateY(-90deg) translateZ(400px) !important;
        transition-delay: .5s;
    }

    #info {
        border: white 5px solid;
        box-sizing: border-box;
        border-radius: 40px 0 40px 40px;
        background: rgba(255, 255, 255, .5);
        height: 460px;
        width: 400px;
        position: absolute;
        right: 35px;
        margin-top: -110px;
        font-size: 20px;
        display: none;
        z-index: 1;
    }

    #close-out {
        border-radius: 50%;
        width: 60px;
        height: 60px;
        text-align: center;
        line-height: 60px;
        color: white;
        font-weight: 900;
        font-size: 40px;
        transition-duration: .5s;
        background-color: rgba(0, 0, 0, .5);
        z-index: 10;
    }

    #close-out:hover {
        background-color: rgba(255, 255, 255, .5);
    }

    #close-out-container:hover {
        box-shadow: 0 0 20px 5px white;
        cursor: pointer;
    }


    @media all and (max-width: 1024px) {
        .cube-container {
            top: 200px;
            width: 150px;
            height: 150px;
        }
        video{
            width: 275%;
        }

        #cube .cube-side {
            font-size: 16px;
            line-height: 28px;
        }

        #cube .front, #cube .right, #cube .left, #cube .back {
            height: 150px;
            width: 150px;
        }

        #cube .front {
            transform: rotateY(0deg) translateZ(150px)
        }

        #cube .right {
            transform: rotateY(90deg) translateZ(150px)
        }

        #cube .left {
            transform: rotateY(-90deg) translateZ(150px)
        }

        #cube .back {
            transform: rotateY(180deg) translateZ(150px)
        }
    }

    @media all and (max-width: 767px) {
        .cube-side.front.highlight {
            transform: rotateY(0deg) translateZ(500px) !important;
        }

        .cube-side.right.highlight  {
            transform: rotateY(90deg) translateZ(500px) !important;
        }

        .cube-side.back.highlight  {
            transform: rotateY(180deg) translateZ(500px) !important;
        }

        .cube-side.left.highlight  {
            transform: rotateY(-90deg) translateZ(500px) !important;
        }
    }



</style>