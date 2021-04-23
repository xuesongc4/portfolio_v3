<template>
  <section id="tech-skills">
    <h2 class="page-title main">Tech Skills</h2>
    <div id="skills-list" :class="{'slideInLeft':slideInLeft}">
      <div class="overlay">
        <div class="list-container">
          <h2 class="page-title">Tech Skills</h2>
          <ul class="tech-skills-list">
            <li v-for="(skill, index) in skillList" :key="index" @mouseover="mouseOnList(index)"
                @mouseleave="mouseOffList(index)" :class="{'active':skill.active}">{{ skill.skill }}
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div id="skills-board" :class="{'slideInRight':slideInRight}">
      <div v-for="(skill, index) in skillList" :key="index" class="skills-block" :class="{'active':skill.active}">
        <div class="skills-block-front" :class="{'dark':lightOrDarkSquare(index) !== -1}">
          <img :src="skill.logoPic" :alt="skill.skill">
        </div>
        <div class="skills-block-back"></div>
      </div>
      <div class="skills-block">
        <div class="skills-block-back"></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Skills",
  props: ['skills', 'pageInView'],
  data() {
    return {
      skillList: this.skills,
      slideInLeft: false,
      slideInRight: false,
      lightSquaresData: [1, 3, 4, 6, 9]
    }
  },
  methods: {
    lightOrDarkSquare($index) {
      return this.lightSquaresData.indexOf($index)
    },
    mouseOnList($index) {
      this.skillList[$index].active = true;
    },
    mouseOffList($index) {
      this.skillList[$index].active = false;
    }
  },
  watch: {
    pageInView: function () {
      const delay = 1500;
      if (this.pageInView) {
        setTimeout(() => {
          this.slideInLeft = true;
          setTimeout(() => this.slideInRight = true, delay - 700)
        }, delay)
      } else {
        this.slideInLeft = false;
        setTimeout(() => this.slideInRight = false, 200)
      }
    }
  }
}
</script>

<style scoped>
#tech-skills {
  background: url('../assets/images/galaxy3-mobile.jpg') no-repeat bottom center fixed;
  background-size: cover;
  max-width: 1920px;
  margin: auto;
}

.page-title {
  color: white;
}

h2.main {
  position: absolute;
  top: 100px;
  left: 50%;
  transform: translateX(-50%);
}

#skills-list {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background: url("../assets/images/coding.jpg") center center no-repeat;
  background-size: cover;
  color: white;
  text-align: left;
  transition-duration: .3s;
}

.overlay {
  background-color: rgba(0, 0, 0, .7);
  height: 100%;
  width: 100%;
}

.tech-skills-list {
  text-align: left;
  width: 350px;
  columns: 1;
}

li {
  font-size: 20px;
  padding: 4px;
  cursor: pointer;
  transition-duration: .3s;
}

li.active {
  padding-left: 25px;
  text-shadow: 2px 2px 10px white;
}

.list-container {
  padding: 60px 30px;

}

#skills-board {
  width: 50%;
  height: 100%;
  position: absolute;
  top: 0;
  right: -50%;
  flex-wrap: wrap;
  transition-duration: .3s;
  perspective: 1000px;
  display: none;
}

.skills-block {
  height: 33.33%;
  width: 25%;
  margin: 0;
  font-size: 0;
  transform-style: preserve-3d;
  position: relative;
  background: transparent;
  border: 1px solid black;
  box-sizing: border-box;
}

.skills-block-front {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 100%;
  position: absolute;
  backface-visibility: hidden;
}

.skills-block-back {
  background: url("../assets/images/red.jpg") bottom center no-repeat fixed;
  background-size: cover;
  height: 100%;
  width: 100%;
  position: absolute;
  z-index: -1;
}

.skills-block.active {
  transform: rotateY(360deg) scale(1.05);
  box-shadow: 0 0 15px 3px white;
  z-index: 100;
  transition-duration: 1s;
}

.skills-block img {
  width: 50px;
}

#skills-list.slideInLeft {
  left: 0;
}

#skills-board.slideInRight {
  right: 0;
}

@media all and (min-width: 640px) {
  .tech-skills-list {
    columns: 2;
  }
}

@media all and (min-width: 768px) {
  #skills-board {
    display: flex;
  }

  #skills-list {
    width: 50%;
    height: 100%;
    top: 0;
    left: -50%;
  }
}

@media all and (min-width: 1024px) {
  #tech-skills {
    background: url('../assets/images/galaxy3.jpg') no-repeat bottom center fixed;
    background-size: cover;
  }

  .tech-skills-list {
    width: 500px;
  }

  li {
    font-size: 28px;
    padding: 8px;
  }

  li.active {
    padding-left: 50px;
  }

  .skills-block img {
    width: 100px;
  }
}

@media all and (min-width: 1300px) {
  .list-container {
    padding: 60px 60px;
  }

  .skills-block img {
    width: 150px;
  }
}

@media (min-width:2500px){
  .list-container {
    padding: 40% 100px;
  }
}

</style>