<template>
    <footer>
        <div class="footer-container">
            <ul class="social">
                <li class="show-for-medium display-none">Connect with me on:</li>
                <li><a target="_blank" href="https://www.linkedin.com/in/xuesongc"><i class="fa fa-linkedin"
                                                                                      aria-hidden="true"></i></a></li>
                <li><a target="_blank" href="https://github.com/xuesongc4"><i class="fa fa-github"></i></a></li>
            </ul>
        </div>
    </footer>
</template>

<script>
    export default {
        name: "Footer"
    }
</script>

<style scoped>
    footer {
        background-color: black;
        color: white;
        width: 100%;
        height: 60px;
        display: block;
        position: absolute;
        font-size: 12px;
        z-index: 2000;
        bottom: -6px;
    }

    .footer-container {
        position: absolute;
        top: 30%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 1200px;
    }

    footer a {
        color: white;
        margin-left: 20px;
        font-weight: 700;
    }

    footer a:hover {
        color: #a42327;
    }

    .social {
        display: flex;
        list-style: none;
    }

    .resume {
        padding-right: 32px;
    }

    @media all and (min-width: 400px) {
        footer {
            font-size: 18px;
        }
    }

    @media all and (min-width: 1024px) {
        footer {
            font-size: 28px;
            height: 80px;
        }

        .footer-container {
            top: 50%;
        }
    }
</style>