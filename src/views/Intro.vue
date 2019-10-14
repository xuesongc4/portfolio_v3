<template>
    <section id="intro">
        <div id="shooting-star-landing">
            <div v-for="(star, $index) in shootingStars" :style="star" :key="$index" class="shootingStar"></div>
        </div>
        <div id="milky-way">
            <div v-for="(star, $index) in milkyStars" :style="star" :key="$index" class="milkyStar"></div>
        </div>
        <div class="intro-content">
            <p class="item-1">Hey there! My name is Jason and I'm a web developer</p>
            <p class="item-2">I enjoy spending time with my friends and family, watching sports, coding and...</p>
            <p class="item-3">looking up at the stars...</p>
        </div>
        <div class="intro-title">
            <h1>Jason Chen</h1>
            <h2>&lt;web_developer&gt;</h2>
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
        font-size: 50px;
    }
    h2{
        position: absolute;
        right: -100px;
        top: 100px;
    }

    .intro-content {
        position: absolute;
        left: 50%;
        top: 20%;
        transform: translateX(-50%);
        font-size: 26px;
        z-index: 10;
    }

    .intro-title {
        position: absolute;
        bottom: 40px;
        right: 30%;
        color: #A42327;
        z-index: 10;
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
        top: -65%;
        left: 45%;
        transform: rotate(145deg);
    }
    #milky-way{
        height: 100vw;
        width: 100vw;
        position: absolute;
        top:50%;
        left: 50%;
        animation: spinningSky linear 240s infinite;
        transform-origin: center center;
    }
</style>
