<template>
    <div>
        <div class="mouse-arrow mouse-up" :class="{show : arrowPosition !== 0}">
            <a id="up-arrow" class="scroll white" :class="{'disabled': arrowDisable}" @click="pageDataTracker('up')"
               v-smooth-scroll="{duration: 2000, container: '#app'}"
            ><span></span><span></span></a>
        </div>
        <div class="mouse-arrow mouse-down" :class="{show : arrowPosition !== 75}">
            <a id="down-arrow" class="scroll white" :class="{'disabled': arrowDisable}" @click="pageDataTracker('down')"
               v-smooth-scroll="{duration: 2000, container: '#app'}"><span></span><span></span></a>
        </div>
        <div class="menu">
            <ul>
                <div :style="{top: arrowPosition+'%'}" class="selected"></div>
                <li :key="index" v-for="(item, index) in menuItems">
                    <a :id="'menu'+item.url" @click="moveArrow(index)" v-smooth-scroll="{duration: 2000, container: '#app'}"
                       :href="item.url">
                        {{item.title}}
                    </a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue'
    import vueSmoothScroll from 'vue2-smooth-scroll'

    Vue.use(vueSmoothScroll);

    export default {
        name: "mainMenu",
        props: ['menuItems'],
        data: function () {
            return {
                arrowPosition: 0,
                upPage: "",
                downPage: "",
                arrowDisable: false
            }
        },
        methods: {
            moveArrow($arrow) {
                this.arrowPosition = $arrow * 25
            },
            pageDataTracker($direction) {
                this.disableSpamClickArrow();
                if ($direction === "up") {
                    if(this.arrowPosition === 25){
                        document.getElementById("menu#intro").click();
                    }else if(this.arrowPosition === 50){
                        document.getElementById("menu#applications").click();
                    }else if(this.arrowPosition === 75){
                        document.getElementById("menu#tech-skills").click();
                    }
                } else if ($direction === "down") {
                    if(this.arrowPosition === 0){
                        document.getElementById("menu#applications").click();
                    }else if(this.arrowPosition === 25){
                        document.getElementById("menu#tech-skills").click();
                    }else if(this.arrowPosition === 50){
                        document.getElementById("menu#contact").click();
                    }
                }

            },
            disableSpamClickArrow(){
                this.arrowDisable = true;
                setTimeout(()=>this.arrowDisable=false,2000);
            },
            handleScroll($event) {
                let windowHeightBreakPoint = 667;
                if(window.innerHeight >= windowHeightBreakPoint){
                    if (($event.deltaY < 0) && (this.arrowPosition !== 0) && (this.arrowDisable==false)) {
                        document.getElementById("up-arrow").click();
                        this.disableSpamClickArrow();
                    } else if (($event.deltaY > 0) && (this.arrowPosition !== 75) && (this.arrowDisable==false)) {
                        document.getElementById("down-arrow").click();
                        this.disableSpamClickArrow();
                    }

                }
            }
        },
        created() {
            window.addEventListener('wheel', this.handleScroll);
        },
        destroyed() {
            window.removeEventListener('wheel', this.handleScroll);
        },
        watch:{
            arrowPosition: function(){
                if (this.arrowPosition === 0) {
                    this.upPage = "";
                    this.downPage = "#applications";
                    this.$emit('inView', false);
                } else if (this.arrowPosition === 25) {
                    this.upPage = "#intro";
                    this.downPage = "#tech-skills";
                    this.$emit('inView', false);
                } else if (this.arrowPosition === 50) {
                    this.upPage = "#applications";
                    this.downPage = "#contact";
                    this.$emit('inView', true);
                } else if (this.arrowPosition === 75) {
                    this.upPage = "#tech-skills";
                    this.downPage = "";
                    this.$emit('inView', false);
                }
            }
        }
    }
</script>

<style scoped>
    .menu {
        position: fixed;
        bottom: 0;
        right: 0;
        background-color: black;
        z-index: 1000;
        text-transform: uppercase;
        padding: 20px;
        opacity: .75;
        font-size: 12px;
        transition-duration: .3s;
        display: none;
    }
    .menu:hover{
        opacity: .75;
    }
    .disabled{
        pointer-events:none;
    }
    ul {
        list-style: none;
        position: relative;
        padding: 0 0 30px 20px;
    }

    li {
        text-align: left;
        padding: 16px 0;
    }

    li:first-of-type {
        padding-top: 0;
    }

    li:last-of-type {
        padding-bottom: 0;
    }

    a {
        color: white;
        font-weight: 700;
        transition-duration: .3s;
    }

    .menu a:hover {
        color: #a42327;
    }

    .selected {
        width: 0;
        height: 0;
        position: absolute;
        left: 0;
        top: 0;
        transition-duration: 2s;
        border-top: 5px solid transparent;
        border-bottom: 5px solid transparent;
        border-left: 10px solid white;
    }

    .mouse-arrow{
        position: absolute;
        display: none;
    }
    .mouse-arrow.mouse-down {
        left: 50%;
        bottom: 40px;
    }

    .mouse-arrow.mouse-up {
        position: absolute;
        left: 50%;
        top: 40px;
    }

    .mouse-arrow.mouse-down a span {
        transform: rotate(-45deg) translateX(-50%);
    }

    .mouse-arrow.mouse-up a span {
        transform: rotate(135deg) translateX(50%);
    }


    .mouse-arrow a.white span {
        border-left: 3px solid #fff;
        border-bottom: 3px solid #fff;
    }

    .mouse-arrow a.black span {
        border-left: 3px solid black;
        border-bottom: 3px solid black;
    }

    .mouse-arrow:hover a.white span, .mouse-arrow:hover a.black span {
        border-left: 3px solid #a42327;
        border-bottom: 3px solid #a42327;
    }

    .mouse-arrow a {
        position: absolute;
        bottom: 20px;
        left: 50%;
        z-index: 2;
        display: inline-block;
        letter-spacing: .1em;
        text-decoration: none;
        transition: opacity .3s;
    }


    .mouse-arrow a span {
        position: absolute;
        top: 0;
        left: 50%;
        width: 20px;
        height: 20px;
        animation: arrow 2.5s infinite;
        opacity: 0;
        box-sizing: border-box;
    }

    .mouse-arrow.mouse-down a span:nth-of-type(1) {
        animation-delay: 0s;
    }

    .mouse-arrow.mouse-down a span:nth-of-type(2) {
        top: 15px;
        animation-delay: .25s;
    }

    .mouse-arrow.mouse-up a span:nth-of-type(1) {
        animation-delay: .25s;
    }

    .mouse-arrow.mouse-up a span:nth-of-type(2) {
        animation-delay: 0s;
        top: 15px;
    }

    .mouse-arrow {
        display: none;
        cursor: pointer;
    }

    #down-arrow, #up-arrow{
        display: none;
    }

    .show {
        display: block;
    }


    @media all and (min-width: 1024px) {
        ul {
            padding: 0 30px 50px;
        }

        li {
            padding: 24px 0
        }
        .menu{
            font-size: 16px;
            opacity: .4;
        }
        .selected {
            border-top: 6px solid transparent;
            border-bottom: 6px solid transparent;
            border-left: 16px solid white;
        }
    }

    @media all and (min-height: 667px) {
        .menu{
            display: block;
        }
        #down-arrow, #up-arrow{
            display: block;
        }
    }
</style>