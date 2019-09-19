<template>
    <div id="intro">
        <div class="intro-content">
            <p class="item-1">Hi there! My name is Jason and I'm a web developer who is based out of Orange County CA.</p>
            <p class="item-2">I enjoy hanging out with my friends and family, sports, coding and...</p>
            <p class="item-3">day dreaming...</p>
        </div>
        <div class="intro-title">
            <h1>Jason Chen</h1>
            <h3>&lt;web_developer&gt;</h3>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Intro',
        props: {
            msg: String
        }
    }
</script>
<style scoped>
    #intro{
        height: 100vh;
        width: 100vw;
        background: url('../assets/stars.png')center center no-repeat;
        background-size: cover;
        position: relative;
    }
    .intro-content{
        position: absolute;
    }
    .intro-title{
        position: absolute;
    }
</style>
