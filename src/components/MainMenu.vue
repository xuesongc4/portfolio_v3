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
        border: 1px solid red;
        transform: translateY(-50%);
    }
    li{
        padding: 20px 0;
    }
</style>