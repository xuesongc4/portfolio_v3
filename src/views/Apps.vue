<template>
    <section id="applications">
        <div class="cube-container" :class="moveCubeData">
            <h2 class="page-title">Applications</h2>
            <div id="cube" :class="[rotateCubeData, cubeSideSelectedData]">
                <div class="cube-side cube-border"
                     :class="[{ 'front': index === 0 }, { 'right': index === 1 }, { 'back': index === 2 }, { 'left': index === 3 }, {highlight:app == selected}]"
                     :key="index" v-for="(app, index) in applications" @click="selected=app; cubeSelect(index)">
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
        <h3 class="caption" @click="cubeDeSelect()">Click on a video for more info...</h3>
    </section>
</template>

<script>
    export default {
        name: "Apps",
        props: ['applications'],
        data: function () {
            return {
                selected: "",
                rotateCubeData: "rotate",
                moveCubeData: "",
                cubeSideSelectedData: ""
            }
        },
        methods: {
            cubeSelect(side) {
                this.rotateCubeData = "";
                this.moveCubeData = "moveCube";

                if (side === 0) {
                    this.cubeSideSelectedData = "show-front"
                } else if (side === 1) {
                    this.cubeSideSelectedData = "show-right"
                } else if (side === 2) {
                    this.cubeSideSelectedData = "show-back"
                } else if (side === 3) {
                    this.cubeSideSelectedData = "show-left"
                }
            },
            cubeDeSelect() {
                this.selected = "";
                setTimeout(() => {
                    this.moveCubeData = "";
                    setTimeout(() => {
                        this.rotateCubeData = "rotate";
                    }, 500)
                }, 500)
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

    .page-title {
        top: -180px;
        left: 50%;
        transform: translateX(-50%);
        color: white;
        position: absolute;
    }

    .moveCube {
        transform: translateX(-350px) !important;
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

    .caption {
        position: absolute;
        bottom: 100px;
        left: 15%;
        color: white;
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
        color: deepskyblue;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }

    #cube .back {
        transform: rotateY(180deg) translateZ(220px);
        color: red;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }

    #cube .right {
        transform: rotateY(90deg) translateZ(220px);
        color: white;
        letter-spacing: -2px;
        width: 220px;
        height: 220px;
        transition-duration: .8s;
    }

    #cube .left {
        transform: rotateY(-90deg) translateZ(220px);
        color: #ffff00;
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
        animation-duration: 12000s;
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

    #info .info-content {
        padding: 0 20px;
        margin-top: -70px;
    }

    .tracker-container .tracker {
        position: absolute;
        bottom: 20px;
        left: 21%;
        width: 220px;
    }

    .side1, .side2, .side3, .side4 {
        display: none;
    }

    @media only screen and (max-width: 1024px) {

        #application .cube {
            top: 180px;
        }

        #cube .front, #cube .right, #cube .left, #cube .back {
            height: 180px;
            width: 180px;
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

        .zoom-front {
            transform: rotateY(0deg) translateZ(280px) !important;
        }

        .zoom-right {
            transform: rotateY(90deg) translateZ(280px) !important;
        }

        .zoom-back {
            transform: rotateY(180deg) translateZ(280px) !important;
        }

        .zoom-left {
            transform: rotateY(-90deg) translateZ(280px) !important;
        }

    }

    @media only screen and (max-width: 767px) {
        #application .cube {
            top: 105px;
        }

        #info {
            background: rgba(255, 255, 255, .7);
            height: 500px;
            width: 315px;
            margin-top: -170px;
            right: 0;
            border-radius: 30px;
        }

        #info h4 {
            font-size: 25px;
        }

        #close-out-container {
            right: -240px;
            top: -5px;
        }

        .zoom-front {
            transform: rotateY(0deg) translateZ(550px) !important;
        }

        .zoom-right {
            transform: rotateY(90deg) translateZ(550px) !important;
        }

        .zoom-back {
            transform: rotateY(180deg) translateZ(550px) !important;
        }

        .zoom-left {
            transform: rotateY(-90deg) translateZ(550px) !important;
        }
    }

</style>