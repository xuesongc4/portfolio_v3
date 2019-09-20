<template>
  <div id="app">
    <MainMenu :menuItems="pages"/>
    <Intro/>
  </div>
</template>

<script>
import Intro from './views/Intro'
import MainMenu from './components/MainMenu'

export default {
  name: 'app',
  components: {
    Intro,
    MainMenu
  },
  data(){
    return {
      pages : [{title:'home',url:'#home'}, {title:'apps',url:'#apps'}, {title:'technical skills',url:'#tech-skills'}, {title:'contact me',url:'#contact'}]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: absolute;
  top:0;
}
body{
  margin:0;
  overflow-x: hidden;
}

@keyframes twinkle {
  0% {
    transform: scale(1, 1);
    background: rgba(0,0,0,0.0);
    animation-timing-function: ease-in;
  }
  60% {
    transform: scale(0.8, 0.8);
    background: rgba(0,0,0,1);
    animation-timing-function: ease-out;
  }
  80% {
    background: rgba(0,0,0,0.00);
    transform: scale(1, 1);
  }
  100% {
    background: rgba(0,0,0,0.0);
    transform: scale(1, 1);
  }
}
</style>
