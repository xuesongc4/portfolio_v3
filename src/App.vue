<template>
  <div id="app">
    <Menu :menuItems="pages"/>
    <Intro/>
  </div>
</template>

<script>
import Intro from './views/Intro'
import Menu from './components/Menu'

export default {
  name: 'app',
  components: {
    Intro,
    Menu
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
  margin-top: 60px;
}
</style>
