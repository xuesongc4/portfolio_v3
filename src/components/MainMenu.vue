<template>
    <div class="menu">
        <ul>
            <div :stlye="{top:arrowPosition}" class="selected"></div>
            <li :key="index" v-for="(item, index) in menuItems"><a :href="item.url">{{item.title}}</a></li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "mainMenu",
        props: ['menuItems'],
        data: function () {
            return {
                arrowPosition:0
            }
        },
        methods: {
            liveArrow(){

            }
        },
        beforeMount() {
            this.liveArrow();
        }
    }
</script>

<style scoped>
    .menu {
        position: fixed;
        bottom: 0;
        right: 0;
        background-color: rgba(0, 0, 0, .7);
        z-index: 1000;
        font-size: 16px;
        text-transform: uppercase;
        padding: 20px;
    }

    ul {
        list-style: none;
        position: relative;
        padding: 0 30px 50px;
    }

    li {
        text-align: left;
        padding: 22px 0;
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
    }

    .selected {
        width: 0;
        height: 0;
        border-top: 6px solid transparent;
        border-bottom: 6px solid transparent;
        border-left: 10px solid white;
        position: absolute;
        left: 0;
        top: 0;
    }
</style>