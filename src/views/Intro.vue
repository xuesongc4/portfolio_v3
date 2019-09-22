<template>
    <section id="intro">
        <div id="shooting-star-landing">
            <div v-for="(star, $index) in shootingStars" :style="star" :key="$index" class="shootingStar"></div>
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
        <div v-for="(star, $index) in stars" :style="star" :key="$index" class="star"></div>
    </section>
</template>

<script>
    export default {
        name: 'Intro',
        data: function () {
            return {
                stars: [],
                shootingStars: []
            }
        },
        methods: {
            twinkleStarLoader() {
                const numberOfStars = 500;
                for (let i = 0; i < numberOfStars; i++) {
                    let size = '2px';
                    const twinkle = 'twinkle ' + ((Math.random() * 3) + 2) + 's linear ' + ((Math.random() * 2)) + 's infinite';
                    const topPx = Math.random() * window.innerHeight + 'px';
                    const leftPx = Math.random() * window.innerWidth + 'px';

                    if(i%10 ==0){
                        size = '5px';
                    }

                    const star = {
                        animation: twinkle,
                        top: topPx,
                        left: leftPx,
                        height: size,
                        width: size
                    }
                    this.stars[i] = star;
                }
            },
            shootingStarLoader() {
                const numberOfStars = 10;
                for (let i = 0; i < numberOfStars; i++) {
                    const randomSpeed = (Math.random() * 10) + 2;
                    const randomStartTime = Math.random() * 3;
                    const shooting = 'shooting ' + randomSpeed + 's linear ' + randomStartTime + 's infinite';
                    const topPx = Math.random() * window.innerHeight + 'px';
                    const leftPx = Math.random() * window.innerWidth*.5 + 'px';

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
            this.twinkleStarLoader();
            this.shootingStarLoader();
        }
    }
</script>
<style scoped>
    #intro {
        background: url('../assets/stars.png') no-repeat bottom center fixed;
        background-size: cover;
        position: relative;
        overflow: hidden;
    }
    h1{
        font-size: 50px;
    }
    h2{
        position: absolute;
        right: -50px;
        top: 80px;
    }

    .intro-content {
        position: absolute;
        left: 50%;
        top: 20%;
        transform: translateX(-50%);
        font-size: 26px;
    }

    .intro-title {
        position: absolute;
        bottom: 10px;
        right: 25%;
        color: #A42327;
    }

    .item-1, .item-2, .item-3{
        white-space: nowrap;
        opacity: 0;
        animation: fadeIn ease-in 1s forwards;
        animation-delay: 3s
    }
    .star {
        position: absolute;
        background: rgba(0, 0, 0, 0);
        border-radius: 5px;
    }
    .shootingStar {
        position: absolute;
        top: 30%;
        right: 30%;
        height: 1px;
        width: 50px;
        background: linear-gradient(-45deg, black, antiquewhite);
        filter: drop-shadow(0 0 6px dimgray);
        opacity: 0;
    }

    #shooting-star-landing {
        height: 50vw;
        width: 50vw;
        border-radius: 50%;
        position: absolute;
        top: -60%;
        left: 30%;
        transform: rotate(145deg);
        z-index: -100;
    }
</style>
