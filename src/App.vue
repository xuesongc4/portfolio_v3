<template>
    <div id="app">
        <MainMenu :menuItems="pages" @inView="inView($event)"/>
        <Intro :starDensity="10" :shooting-star-density="1"/>
        <Applications :applications="apps"/>
        <Skills :skills="skills" :pageInView="skillsPageInView"></Skills>
        <Contact></Contact>
    </div>
</template>

<script>
    import MainMenu from './components/MainMenu'
    import Intro from './views/Intro'
    import Applications from './views/Applications'
    import Skills from './views/Skills'
    import Contact from "./views/Contact";

    export default {
        name: 'app',
        components: {
            Intro,
            MainMenu,
            Applications,
            Skills,
            Contact
        },
        data() {
            return {
                skillsPageInView: false,
                pages: [
                    {title: 'About Me', url: '#intro'},
                    {title: 'applications', url: '#applications'},
                    {title: 'tech skills', url: '#tech-skills'},
                    {title: 'contact me', url: '#contact'}
                ],
                apps: [
                    {
                        title: 'Tar Football',
                        videoUrl: require('./assets/videos/tar.mp4'),
                        url: 'https://www.tarfootball.com',
                        info: 'The official website of the Newport Harbor High School Football Team. This WordPress site has a completely custom theme that I developed. The site covers all of the latest happenings surrounding the team. The store is a Shopify store with all of the hottest Tar merchandise. The sales and sponsorships generated between these sites allow the boys to keep playing hard! Go Tars!'
                    },
                    {
                        title: 'Tar Football App',
                        videoUrl: require('./assets/videos/tarfootball-app.mp4'),
                        gitUrl: 'https://github.com/xuesongc4/Tarfootball-App',
                        url: 'https://tarfootball.netlify.com/',
                        info: 'A Vue web app that pulls data from the tarfootball.com WordPress REST API. This app has the latest Tar Football news, the schedule and the current player roster. This application uses Vuex for state management and Axios to communicate with the WordPress API.'
                    },
                    {
                        title: 'Just Food For Dogs',
                        videoUrl: require('./assets/videos/jffd.mp4'),
                        url: 'https://www.justfoodfordogs.com/',
                        info: 'A Nop Commerce based website where I handled a majority of the front end development. The site had some interesting challenges that made for a fun and unique build. The site uses Bootstrap for the homepage and Foundation for the interior pages(long story...) with a .Net backend. P.S. I love dogs!'
                    },
                    {
                        title: 'Tic Tac Remix',
                        videoUrl: require('./assets/videos/tictacremix.mp4'),
                        gitUrl: 'https://github.com/xuesongc4/tic-tac-remix2.0',
                        url: 'https://tic-tac-remix.netlify.com/',
                        info: 'A DJ/music themed tic-tac-toe game that introduces a musical twist the the classic game. Each player\'s move adds layers of music to the playing sound track. This game was created using vanilla JS + jQuery.'
                    }

                ],
                skills: [
                    {skill: 'Vue.js', logoPic: require('./assets/logo/vue.png')},
                    {skill: 'JavaScript', logoPic: require('./assets/logo/JavaScript.png')},
                    {skill: 'jQuery', logoPic: require('./assets/logo/jQuery.png')},
                    {skill: 'HTML', logoPic: require('./assets/logo/HTML5.png')},
                    {skill: 'CSS', logoPic: require('./assets/logo/CSS3.png')},
                    {skill: 'Sass', logoPic: require('./assets/logo/Sass.png')},
                    {skill: 'PHP', logoPic: require('./assets/logo/php.png')},
                    {skill: 'Foundation', logoPic: require('./assets/logo/Foundation.png')},
                    {skill: 'Bootstrap', logoPic: require('./assets/logo/Bootstrap.png')},
                    {skill: 'Git', logoPic: require('./assets/logo/git.png')},
                    {skill: 'WordPress', logoPic: require('./assets/logo/WordPress.png')}
                ]
            }
        },
        methods: {
            inView($event) {
                this.skillsPageInView = $event;
            },
            skillActiveInit() {
                this.skills.forEach(($prop, $index) => this.$set(this.skills[$index], 'active', false))
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
        height: 667px;
    }

    .page_title {
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

    .mobile-warning {
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

    .display-none {
        display: none;
    }

    @media all and (min-width: 640px) {
        .hide-for-medium {
            display: none;
        }

        .show-for-medium {
            display: block;
        }
    }

    @media all and (min-width: 1024px) {
        .hide-for-large {
            display: none;
        }

        .show-for-medium {
            display: block;
        }
    }

    @media all and (min-height: 667px) {
        #app {
            height: 100vh;
            overflow-y: hidden;
        }

        ::-webkit-scrollbar {
            display: none;
        }
    }

    @media screen and (max-width: 812px) and (orientation: landscape) {
        #app {
            display: none;
        }

        .mobile-warning {
            display: block;
            padding: 20px;
            font-size: 20px;
        }
    }

    @media screen and (max-height: 500px) {
        #app {
            display: none;
        }

        .mobile-warning {
            display: block;
            padding: 20px;
            font-size: 20px;
        }
    }
</style>
