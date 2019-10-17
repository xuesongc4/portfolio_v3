<template>
    <div id="app">
        <MainMenu :menuItems="pages"  @inView="inView($event)"/>
        <Intro :starDensity="10" :shooting-star-density="1"/>
        <Apps :applications="apps"/>
        <Skills :skills="skills" :pageInView="skillsPageInView"></Skills>
        <Contact></Contact>
        <Footer></Footer>
    </div>
</template>

<script>
    import MainMenu from './components/MainMenu'
    import Intro from './views/Intro'
    import Apps from './views/Apps'
    import Skills from './views/Skills'
    import Contact from "./views/Contact";
    import Footer from './components/Footer'

    export default {
        name: 'app',
        components: {
            Intro,
            MainMenu,
            Apps,
            Skills,
            Contact,
            Footer

        },
        data() {
            return {
                skillsPageInView:false,
                pages: [
                    {title: 'About Me', url: '#intro'},
                    {title: 'applications', url: '#applications'},
                    {title: 'tech skills', url: '#tech-skills'},
                    {title: 'contact me', url: '#contact'}
                ],
                apps: [
                    {
                        title: 'iBet',
                        videoUrl: require('./assets/videos/iBet.mp4'),
                        gitUrl: '#gitDemo1',
                        url: '#demo1',
                        info: 'A mobile friendly web application that allows for a user to create an account and make simulated sports bets with real odds. Results are logged and graphed under that account so that long term results can be analyzed.'
                    },
                    {
                        title: 'Moduulis',
                        videoUrl: require('./assets/videos/moduulis.mp4'),
                        gitUrl: '#gitDemo2',
                        url: '#demo2',
                        info: 'A WordPress based mobile friendly e-commerce (Woocomerce) website built around customizable snack stadiums. The site includes a blog, a vlog and a functional store.'
                    },
                    {
                        title: 'Tic Tac Remix',
                        videoUrl: require('./assets/videos/tictacremix.mp4'),
                        gitUrl: '#gitDemo3',
                        url: '#demo3',
                        info: 'A DJ/music themed tic-tac-toe game that introduces a musical twist the the classic game. Each player\'s turn adds layers of music to the playing sound track.'
                    },
                    {
                        title: 'Reading For Dummies',
                        videoUrl: require('./assets/videos/reading.mp4'),
                        gitUrl: '#gitDemo4',
                        url: '#demo4',
                        info: ' The average person reads at about 300 words per a minute, however by removing the need to move your eyes you can read much faster. Take a look at this app that helps slow readers like myself read at amazingly high speeds!'
                    }
                ],
                skills:[
                    {skill: 'Vue.js', logoPic: require('./assets/logo/vue.png')},
                    {skill: 'JavaScript', logoPic: require('./assets/logo/JavaScript.png')},
                    {skill:'jQuery', logoPic: require('./assets/logo/jQuery.png')},
                    {skill:'HTML', logoPic: require('./assets/logo/HTML5.png')},
                    {skill:'CSS', logoPic: require('./assets/logo/CSS3.png')},
                    {skill:'Sass', logoPic:require('./assets/logo/Sass.png')},
                    {skill:'php', logoPic:require('./assets/logo/php.png')},
                    {skill:'Foundation', logoPic:require('./assets/logo/Foundation.png')},
                    {skill:'BootStrap', logoPic:require('./assets/logo/Bootstrap.png')},
                    {skill:'git', logoPic:require('./assets/logo/git.png')},
                    {skill:'WordPress', logoPic:require('./assets/logo/WordPress.png')}
                ]
            }
        },
        methods:{
            inView($event){
                this.skillsPageInView = $event;
            },
            skillActiveInit(){
                this.skills.forEach(($prop,$index)=> this.$set(this.skills[$index], 'active', false))
            }
        },
        beforeMount() {
            this.skillActiveInit();
        }
    }
</script>

<style>
    @import url("https://fonts.googleapis.com/css?family=Oswald&display=swap");

    #app {
        font-family: Helvetica, sans-serif;
        font-size: 20px;
        text-align: center;
        height: 100vh;
        overflow-y: hidden;
    }
    .page_title{
        font-size: 50px;
        font-weight: 700;
    }

    a {
        text-decoration: none;
    }

    h1 {
        font-family: 'Oswald', sans-serif;
    }

    h2, h3, h4, h5, h6 {
        font-family: Helvetica, sans-serif;
    }

    body {
        margin: 0;
        overflow-x: hidden;
    }

    section {
        height: 100vh;
        width: 100vw;
        position: relative;
    }

    .page-title {
        font-size: 50px;
        font-weight: 700;
    }

    ::-webkit-scrollbar {
        display: none;
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

    @keyframes spinningSky {
        0% {
            transform: translate(-50%, -50%) rotate(0);

        }
        100% {
            transform: translate(-50%, -50%) rotate(-360deg);
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

    @keyframes arrow {
        0% {
            opacity: 0;
        }
        50% {
            opacity: 1;
        }
        100% {
            opacity: 0;
        }
    }

    .display-none{
        display: none;
    }

    @media all and (min-width: 640px) {
        .hide-for-medium{
            display: none;
        }
        .show-for-medium{
            display: block;
        }
    }
    @media all and (min-width: 1024px) {
        .hide-for-large{
            display: none;
        }
        .show-for-medium{
            display: block;
        }
    }
</style>
