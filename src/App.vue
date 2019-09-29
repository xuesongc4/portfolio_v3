<template>
    <div id="app">
        <MainMenu :menuItems="pages"/>
        <Intro :starDensity="1"/>
        <Apps :applications="apps"/>
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
                    {title: 'contact me', url: '#contact'}
                    ]
                ,
                apps: [
                    {
                        title: 'iBet',
                        videoUrl: require('./videos/iBet.mp4'),
                        gitUrl: '#gitDemo1',
                        url: '#demo1',
                        info: 'za za'
                    },
                    {
                        title: 'Moduulis',
                        videoUrl: require('./videos/moduulis.mp4'),
                        gitUrl: '#gitDemo2',
                        url: '#demo2',
                        info: 'blah blah'
                    },
                    {
                        title: 'Tic Tac Remix',
                        videoUrl: require('./videos/tictacremix.mp4'),
                        gitUrl: '#gitDemo3',
                        url: '#demo1',
                        info: 'heh ehehe'
                    },
                    {
                        title: 'Reading For Dummies',
                        videoUrl: require('./videos/reading.mp4'),
                        gitUrl: '#gitDemo4',
                        url: '#demo4',
                        info: 'chehehehe',
                    }
                ]
            }
        }
    }
</script>

<style>
    @import url("https://fonts.googleapis.com/css?family=Oswald&display=swap");
    @import url("https://fonts.googleapis.com/css?family=Montserrat &display=swap");

    #app {
        font-family: 'Montserrat ', Helvetica, sans-serif;
        font-size: 20px;
        text-align: center;
    }

    h1{
        font-family: 'Oswald', Helvetica, sans-serif;
    }
    h2, h3, h4, h5, h6 {
        font-family: 'Montserrat', Helvetica, sans-serif;
    }

    body {
        margin: 0;
        overflow-x: hidden;
    }

    section {
        height: 100vh;
        width: 100vw;
    }

    .page-title{
        font-size: 50px;
        font-weight: 700;
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

    @keyframes rotate-cube {
        100% {
            transform: rotateY(-36000deg);
        }
    }

    ::-webkit-scrollbar {
        display: none;
    }
</style>
