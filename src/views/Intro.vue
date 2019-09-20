<template>
    <div id="intro">
        <div class="intro-content">
            <p class="item-1">Hi there! My name is Jason and I'm a web developer who is based out of Orange County
                CA.</p>
            <p class="item-2">I enjoy hanging out with my friends and family, sports, coding and...</p>
            <p class="item-3">looking up at the stars...</p>
        </div>
        <div class="intro-title">
            <h1>Jason Chen</h1>
            <h3>&lt;web_developer&gt;</h3>
        </div>
        <div v-for="(star, $index) in stars" :style="star" :key="$index" class="star" ></div>
    </div>
</template>

<script>
    export default {
        name: 'Intro',
        data: function(){
            return{
                stars:[]
            }
        },
        methods: {
            twinkleStarLoader() {
                const numberOfStars = 100;
                for (let i = 0; i < numberOfStars; i++) {
                    const twinkle = 'twinkle '+((Math.random()*5) + 5)+'s linear '+((Math.random()*5)+2)+'s infinite';
                    const topPx = Math.random()*window.innerHeight+'px';
                    const leftPx = Math.random()*window.innerWidth+'px';
                    const star = {
                        animation: twinkle,
                        top: topPx,
                        left: leftPx
                    }
                    this.stars[i] = star;
                }
            }
        },
        beforeMount(){
            this.twinkleStarLoader()
        },
    }
</script>
<style scoped>
    #intro {
        height: 100vh;
        width: 100vw;
        background: url('../assets/stars.png') center center no-repeat;
        background-size: cover;
        position: relative;
    }

    .intro-content {
        position: absolute;
    }

    .intro-title {
        position: absolute;
    }

    .star {
        position: absolute;
        width: 4px;
        height: 4px;
        background: rgba(0,0,0,0);
        border-radius: 5px;
    }

</style>
