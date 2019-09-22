<template>
    <div class="menu">
        <ul>
           <li :key="index" v-for="(item, index) in menuItems"><a :href="item.url">{{item.title}}</a></li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "mainMenu",
        props: ['menuItems'],
        }
</script>

<style scoped>
    .menu{
        position: fixed;
        top:50%;
        right: 100px;
        transform: translateY(-50%);
        background-color: rgba(255,255,255,.7);
        z-index: 1000;
        font-size: 16px;
    }
    li{
        padding: 20px 0;
    }
</style>