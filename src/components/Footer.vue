<template>
    <footer>
        <div class="footer-container">
            <ul class="social">
                <li class="show-for-medium display-none">Connect with me on:</li>
                <li><a target="_blank" href="https://www.linkedin.com/in/jason-chen-619b2852"><i class="fa fa-linkedin" aria-hidden="true"></i></a></li>
                <li><a target="_blank" href="https://www.facebook.com/profile.php?id=6026042"><i
                        class="fa fa-facebook"></i></a></li>
                <li><a target="_blank" href="https://github.com/xuesongc4"><i class="fa fa-github"></i></a></li>
            </ul>
            <div class="resume"><a target="_blank" href="documents/resume.pdf">Check out my Resume</a></div>
        </div>
    </footer>
</template>

<script>
    export default {
        name: "Footer"
    }
</script>

<style scoped>
    footer{
        background-color: black;
        color: white;
        bottom: 40px;
        width: 100%;
        height: 40px;
        display: block;
        position: relative;
        font-size: 16px;
        z-index: 2000;
    }
    .footer-container{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 1200px;
    }
    footer a{
        color: white;
        margin-left: 20px;
        font-weight: 700;
    }
    footer a:hover{
        color: #a42327;
    }
    .social{
        display: flex;
        list-style: none;
    }
    .resume{
        padding-right: 32px;
    }
    @media all and (min-width: 640px) {
        footer{
            font-size: 20px;
        }
    }
    @media all and (min-width: 1024px) {
        footer{
            font-size: 28px;
            height: 80px;
            bottom: 75px;
        }
    }
</style>