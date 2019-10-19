<template>
    <section id="intro">
        <div id="shooting-star-landing">
            <div v-for="(star, $index) in shootingStars" :style="star" :key="$index" class="shootingStar"></div>
        </div>
        <div id="milky-way">
            <div v-for="(star, $index) in milkyStars" :style="star" :key="$index" class="milkyStar"></div>
        </div>
        <div class="intro-content">
            <p class="item-1">Hey there!<br class="hide-for-large"> My name is Jason<br class="hide-for-large"> and I'm a web developer</p>
            <p class="item-2">I enjoy spending time with my<br class="hide-for-large"> friends and family,<br class="hide-for-large"> watching sports, coding and...</p>
            <p class="item-3">looking up at the stars...</p>
        </div>
        <div class="intro-title">
            <h1>Jason Chen</h1>
            <h2>&lt;web_developer&gt;</h2>
        </div>
        <div class="disclaimer">
            For best viewing experience please view on fullscreen.
        </div>
    </section>
</template>

<script>
    export default {
        name: 'Intro',
        props: ['starDensity','shootingStarDensity'],
        data: function () {
            return {
                milkyStars: [],
                shootingStars: [],
                screenSize : null
            }
        },
        methods: {
            screenSizeCalc() {
                const height = window.innerHeight;
                const width = window.innerWidth;
                let screenSize = null;
                if (height >= width) {
                    screenSize = height;
                } else {
                    screenSize = width;
                }
                this.screenSize = screenSize;
            },
            milkyStarLoader() {
                const numberOfStars = 100 * this.starDensity;
                for (let i = 0; i < numberOfStars; i++) {
                    let size = '2px';
                    const topPx = Math.random() * this.screenSize+ 'px';
                    const leftPx = Math.random() * this.screenSize + 'px';

                    if(i%15 ==0){
                        size = '5px';
                    }

                    const milkyStar = {
                        top: topPx,
                        left: leftPx,
                        height: size,
                        width: size
                    }
                    this.milkyStars[i] = milkyStar;
                }
            },
            shootingStarLoader() {
                const numberOfStars = 10 * this.shootingStarDensity;
                for (let i = 0; i < numberOfStars; i++) {
                    const randomSpeed = (Math.random() * 10) + 2;
                    const randomStartTime = Math.random() * 3;
                    const shooting = 'shooting ' + randomSpeed + 's linear ' + randomStartTime + 's infinite';
                    const topPx = Math.random() * window.innerHeight *.7 + 'px';
                    const leftPx = Math.random() * window.innerWidth*.3 + 'px';

                    const shootingStar = {
                        animation: shooting,
                        top: topPx,
                        left: leftPx
                    }
                    this.shootingStars[i] = shootingStar;
                }
            }
        },
        beforeMount() {
            this.screenSizeCalc();
            this.milkyStarLoader();
            this.shootingStarLoader();
        }
    }
</script>
<style scoped>
    #intro {
        background: url('../assets/images/stars.png') no-repeat bottom center fixed;
        background-size: cover;
        position: relative;
        overflow: hidden;
        background-color: white;
    }
    h1{
        display: inline-block;
        font-size: 28px;
    }
    h2{
        position: absolute;
        display: inline-block;
        right: -40px;
        top: 60px;
        font-size: 16px;
    }
    .disclaimer{
        font-size: 14px;
        color: black;
        position: absolute;
        top: 10px;
        left: 10px;
    }
    .intro-content {
        position: absolute;
        left: 50%;
        top: 10%;
        transform: translateX(-50%);
        font-size: 24px;
        line-height: 1.3;
        z-index: 10;
        background-color: rgba(255,255,255,.65);
    }

    .intro-title {
        position: absolute;
        color: #A42327;
        z-index: 10;
        bottom: 40px;
        left: 5%;
    }
    .item-1, .item-2, .item-3{
        white-space: nowrap;
        opacity: 0;
        animation: fadeIn ease-in 2s forwards;
        animation-delay: 1s
    }
    .milkyStar{
        position: absolute;
        border-radius: 50%;
        background-color: black;
    }
    .shootingStar {
        position: absolute;
        top: 30%;
        right: 30%;
        height: 1px;
        width: 35px;
        background: linear-gradient(-45deg, black, antiquewhite);
        filter: drop-shadow(0 0 6px dimgray);
        opacity: 0;
    }

    #shooting-star-landing {
        height: 40vw;
        width: 20vw;
        position: absolute;
        transform: rotate(145deg);
        top: 0%;
        left: 100%;
    }
    #milky-way{
        height: 200vw;
        width: 200vw;
        position: absolute;
        top:50%;
        left: 50%;
        animation: spinningSky linear 240s infinite;
        transform-origin: center center;
    }

    @media all and (min-width: 640px) {
        h1{
            font-size: 36px;
        }
        h2{
            right: -100px;
            top: 60px;
            font-size: 24px;
        }
        .intro-title {
            bottom: 50px;
            left: 20%;
        }
        #milky-way {
            top: 40%;
            height: 100vw;
            width: 100vw;
        }
        #shooting-star-landing {
            top: -10%;
            left: 75%;
        }
        .intro-content {
            font-size: 26px;
        }
    }

    @media all and (min-width: 1024px) {
        .disclaimer{
            font-size: 16px;
            color: white;
            opacity: .5;
            top: unset;
            bottom: 10px;
            left: 10px;
        }
        h1{
            font-size: 50px;
        }
        h2{
            right: -100px;
            top: 100px;
        }
        .intro-content{
            top: 20%;
        }
        .intro-title {
            bottom: 40px;
            right: 30%;
            left: unset;
        }
        #milky-way {
            height: 100vw;
            width: 100vw;
            top: 50%;
        }
        #shooting-star-landing {
            top: -60%;
            left: 50%;
        }
    }
</style>
