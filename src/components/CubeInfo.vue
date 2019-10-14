<template>
    <div class="info-container">
        <div id="info"
             :class="[{'horizontal': infoHorizontal === true} , {'vertical': infoVertical === true}, {'show': infoShow === true}]">
            <div :key="index" v-for="(info, index) in applications" class="app-info"
                 :class="{'show fadeIn': sideShow === index }">
                <h4>{{info.title}}</h4>
                <div class="info">
                    <p>
                        {{info.info}}
                    </p>
                    <div class="links" :class="[{'show': (sideShow === index && bubble === true) } ]">
                        <a class="button link" target="_blank" :href="info.url">Live Site</a>
                        <a class="button github" target="_blank" :href="info.gitUrl">GitHub</a>
                    </div>
                </div>
            </div>
        </div>
        <div class="bubble-container" :class="{'bubbleShow': bubble === true}">
            <div :key="index" v-for="(info, index) in applications" class="bubble"
                 :class="{'selected': sideShow === index }" @click="changeSide(index)"></div>
        </div>
        <div class="close-button-container" :class="{'show': closeButton === true}">
            <div @click="closeInfo" id="close-button">X</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CubeInfo",
        props: ['applications', 'side'],
        data() {
            return {
                timeInterval: 500,
                sideShow: this.side,
                closeButton: false,
                infoHorizontal: false,
                infoVertical: false,
                bubble: false,
                infoShow: false
            }
        },
        watch: {
            side: function (newSide) {
                this.sideShow = newSide.data;
                this.openInfo();
            }
        },
        methods: {
            openInfo() {
                this.infoShow = true;
                setTimeout(() => {
                    this.closeButton = true;
                    this.infoHorizontal = true;
                    setTimeout(() => {
                        this.infoVertical = true;
                        setTimeout(() => {
                            this.bubble = true;
                        }, this.timeInterval)
                    }, this.timeInterval)
                }, this.timeInterval/10)
            },
            closeInfo() {
                this.$emit("closeInfo", {data: 'close'});
                this.bubble = false;
                this.infoVertical = false;
                setTimeout(() => {
                    this.infoHorizontal = false;
                    setTimeout(() => {
                        this.closeButton = false;
                        this.infoShow = false;
                    }, this.timeInterval)
                }, this.timeInterval)
            },
            changeSide(side) {
                this.sideShow = side;
                this.$emit("changeSide", side)
            }
        }
    }
</script>

<style scoped>
    .bubble-container {
        position: absolute;
        bottom: 25px;
        width: 100%;
        height: 50px;
        display: none;
        justify-content: center;
        align-items: center;
    }

    .bubble {
        border: 2px solid white;
        border-radius: 50%;
        width: 12px;
        height: 12px;
        margin: 0 18px;
        transition-duration: .3s;
        cursor: pointer;
    }
    .bubble.selected {
        border-width: 3px;
        box-shadow: 0 0 20px 5px white;
        background-color: white;
        pointer-events: none;
    }

    .bubbleShow{
        display: flex;
    }

    .links {
        position: absolute;
        bottom: 0px;
        display: none;
        z-index: 10;
    }

    .info-container {
        position: absolute;
        right: 450px;
        top: 150px;
    }

    #info {
        box-sizing: border-box;
        border-radius: 40px 0 40px 40px;
        background: rgba(255, 255, 255, .6);
        border: white solid 5px;
        height: 0;
        width: 0;
        display: none;
        font-size: 20px;
        text-align: left;
        line-height: 1.3;
        transition: all .5s linear;
        overflow: hidden;
        position: relative;
    }

    h4 {
        font-size: 30px;
        margin: 10px 0;
    }

    .github {
        background-color: #77AF5B;
    }

    .link {
        background-color: #A42327
    }

    .button {
        padding: 10px 20px;
        min-width: 85px;
        transition-duration: .5s;
        text-align: center;
        border-radius: 8px;
        display: inline-block;
        border: solid 2px white;
        opacity: .5;
        font-size: 12px;
        text-transform: uppercase;
        color: white;
        margin-right: 10px;
    }

    .button:hover {
        opacity: 1;
        box-shadow: 0 0 20px 5px white;
    }

    .app-info {
        opacity: 0;
        transition-duration: .5s;
        position: absolute;
        margin: 10px 20px;
        height: 80%;
    }

    .close-button-container {
        border: solid white 5px;
        border-radius: 50%;
        width: 60px;
        height: 60px;
        background: url('../assets/images/galaxy3.jpg') no-repeat center center fixed;
        position: absolute;
        top: -33px;
        right: -33px;
        display: none;
    }

    #close-button {
        border-radius: 50%;
        width: 60px;
        height: 60px;
        text-align: center;
        line-height: 60px;
        color: white;
        font-weight: 700;
        font-size: 40px;
        transition-duration: .3s;
        background-color: rgba(0, 0, 0, .5);
        z-index: 10;
    }

    #close-button:hover {
        background-color: rgba(255, 255, 255, .5);
    }

    .close-button-container:hover {
        box-shadow: 0 0 20px 5px white;
        cursor: pointer;
    }

    .show {
        display: block !important;
    }

    .fadeIn {
        opacity: 1;
        transition-delay: .5s;
    }

    #info.horizontal {
        width: 400px;
    }

    #info.vertical {
        height: 460px;
    }
</style>