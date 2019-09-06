<template>
    <div class="menu">
        <ul>
            <li>home</li>
            <li>apps</li>
            <li>technical skills</li>
            <li>contact me</li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "menu"
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