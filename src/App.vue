<template>
    <div id="app">
        <MainMenu :menuItems="pages"/>
        <Intro/>
        <Apps/>
    </div>
</template>

<script>
    import MainMenu from './components/MainMenu'
    import Intro from './views/Intro'
    import Apps from './views/Apps'

    export default {
        name: 'app',
        components: {
            Intro,
            MainMenu,
            Apps
        },
        data() {
            return {
                pages: [
                        {title: 'home', url: '#intro'},
                        {title: 'apps', url: '#applications'},
                        {title: 'technical skills', url: '#tech-skills'},
                        {title: 'contact me', url: '#contact'}]
            }
        }
    }
</script>

<style>
    @import url("https://fonts.googleapis.com/css?family=Oswald&display=swap");
    @import url("https://fonts.googleapis.com/css?family=Montserrat &display=swap");

    #app {
        font-family: 'Montserrat ', Helvetica, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        position: absolute;
        top: 0;
        font-size: 20px;
    }

    h1, h2, h3, h4, h5, h6 {
        font-family: 'Oswald', Helvetica, sans-serif;
    }

    body {
        margin: 0;
        overflow-x: hidden;
    }

    section {
        height: 100vh;
        width: 100vw;
    }

    @keyframes twinkle {
        0% {
            transform: scale(1, 1);
            background: rgba(0, 0, 0, 0.0);
            animation-timing-function: ease-in;
        }
        60% {
            transform: scale(0.8, 0.8);
            background: rgba(0, 0, 0, 1);
            animation-timing-function: ease-out;
        }
        80% {
            background: rgba(0, 0, 0, 0.00);
            transform: scale(1, 1);
        }
        100% {
            background: rgba(0, 0, 0, 0.0);
            transform: scale(1, 1);
        }
    }

    @keyframes shooting {
        0% {
            transform: translateX(0);
            opacity: 0;
        }
        3% {
            opacity: .3;
        }
        7% {
            opacity: .7;
        }
        10% {
            opacity: 1;
        }
        100% {
            transform: translateX(1000px);
        }
    }

    @keyframes fadeIn {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }
</style>
