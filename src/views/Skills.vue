<template>
    <section id="tech-skills">
        <h2 class="page-title main">Tech Skills</h2>
        <div id="skills-list" :class="{'slideInLeft':slideInLeft}">
            <div class="overlay">
                <div class="list-container">
                    <h2 class="page-title">Tech Skills</h2>
                    <ul class="tech-skills-list">
                        <li v-for="(skill, index) in skillList" :key="index">{{skill.skill}}</li>
                    </ul>
                </div>
            </div>
        </div>
        <div id="skills-board" :class="{'slideInRight':slideInRight}">
            <div v-for="(skill, index) in skillList" :key="index" class="skills-block" :class="{'dark':lightOrDarkSquare(index) !== -1}">
                <img :src="skill.logoPic" :alt="skill.skill">
            </div>
            <div class="skills-block dark"></div>
        </div>
    </section>
</template>

<script>
    export default {
        name: "Skills",
        props: ['skills', 'pageInView'],
        data(){
            return {
                skillList: this.skills,
                slideInLeft : false,
                slideInRight: false,
                lightSquaresData : [1,3,4,6,9]
            }
        },
        methods:{
            lightOrDarkSquare($index){
                return this.lightSquaresData.indexOf($index)
            }
        },
        watch: {
            pageInView: function(){
                const delay = 1500;
                if(this.pageInView){
                    setTimeout(()=>{
                        this.slideInLeft = true;
                        setTimeout(()=>this.slideInRight = true,delay-700)
                    },delay)
                }else{
                    this.slideInLeft = false;
                    setTimeout(()=>this.slideInRight = false, 200)
                }
            }
        }
    }
</script>

<style scoped>
    #tech-skills{
        background: url("../assets/images/galaxy3.jpg") bottom center no-repeat fixed;
    }
    .page-title{
        color: white;
    }
    h2.main{
        position: absolute;
        top: 100px;
        left: 50%;
        transform: translateX(-50%);
    }
    #skills-list{
        width: 50%;
        height: 100%;
        position: absolute;
        top: 0;
        left: -50%;
        background: url("../assets/images/coding.jpg") center center no-repeat;
        background-size: cover;
        color: white;
        text-align: left;
        transition-duration: .3s;
    }
    .overlay{
        background-color: rgba(0,0,0,.7);
        height: 100%;
        width: 100%;
    }
    .tech-skills-list{
        text-align: left;
        width: 500px;
        columns:2;
    }
    li{
        font-size: 28px;
        padding: 8px;
        cursor: pointer;
        transition-duration: .3s;
    }
    li:hover{
        padding-left: 50px;
        text-shadow: 2px 2px 10px white;
    }
    .list-container{
        padding: 60px;
    }
    #skills-board{
        width: 50%;
        height: 100%;
        position: absolute;
        top: 0;
        right: -50%;
        display:flex;
        flex-wrap: wrap;
        transition-duration: .3s;
    }
    .skills-block{
        height: 33.33%;
        width: 25%;
        background-color: #EA6C7C;
        margin: 0;
        font-size: 0;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .skills-block img{
        width: 150px;
    }
    .dark{
        background-color: #a42327;
    }
    #skills-list.slideInLeft{
        left: 0;
    }
    #skills-board.slideInRight{
        right: 0;
    }
</style>