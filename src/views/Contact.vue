<template>
    <section id="contact">
        <div class="map-bg"></div>
        <div class="stars-bg">
            <div class="container">
                <div class="contact-form">
                    <div class="page_title">
                        Connect With Me
                    </div>
                    <div class="contact-form-container">
                        <img src="../assets/me_cartoon.png">
                        <form>
                            <div class="input-container">
                                <input type="text" name="name" class="form-control" placeholder="Name*">
                                <input type="email" name="email" class="form-control" placeholder="Email*">
                            </div>
                            <div class="input-container">
                                 <textarea name="body" rows='4' cols="25" type="text"
                                           class="form-control textarea-control"
                                           placeholder="Message*"></textarea>
                            </div>
                            <div class="button-container">
                                <button type="submit" name="submit" class="submit" onclick="send_email(event)">
                                    <div class="send">
                                        SEND
                                    </div>
                                    <div class="loader-container">
                                        <div class="loader"></div>
                                    </div>
                                </button>
                                <div class="send-message"></div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: "Contact"
    }
</script>

<style scoped>
    .map-bg{
        background: url("../assets/map.png")center center no-repeat;
        background-size: cover;
        height: 100vh;
        width: 100vw;
        z-index: -10;
        position: fixed;
        bottom: 0;
    }
    .stars-bg{
        background: url("../assets/stars2.png") no-repeat;
        background-position-x: center;
        background-position-y: -220px;
        height: 100vh;
        width: 100vw;
        position: absolute;
        bottom: 0;
    }

    #contact {
        position: relative;
    }

    .contact-form-container {
        width: 70%;
        margin: auto;
    }

    .contact-form {
        max-width: 1000px;
        width: 100%;
        border: 5px solid #A42327;
        border-radius: 20px;
        background-color: rgba(0, 0, 0, .5);
        position: absolute;
        top: 35%;
        left: 42%;
        transform: translate(-50%, -30%);
        font-size: 20px;
        box-shadow: 0 0 50px 5px black;
    }

    .input-container {
        display: flex;
    }

    .input-container input, .input-container textarea {
        margin: 10px;
        border: 2px solid transparent;

    }

    .contact-form .page_title {
        margin-top: 30px;
        color: white;
    }

    .contact-form img {
        height: 170px;
        width: auto;
        border-radius: 50%;
        border: 5px solid #A42327;
        background-color: white;
        background-color: rgba(255, 255, 255, .7);
        display: block;
        margin: 20px auto;
    }

    .form-control {
        background-color: rgba(255, 255, 255, .7);
        border-radius: 4px;
        color: #111;
        display: block;
        font-size: 15px;
        height: 30px;
        padding: 6px 12px;
        margin-left: -12px;
        width: 100%;
        font-family: 'Montserrat', sans-serif;
        border: none;
        margin-bottom: 20px;
    }

    .form-control:focus {
        border: 2px solid #A42327;
        outline-width: 0;
        box-shadow: 0 0 10px 1px #A42327;
    }

    ::-webkit-placeholder, ::-o-placeholder, ::-moz-placeholder {
        font-family: 'Montserrat', sans-serif;
        color: #d9d9d9;
        font-size: 15px;
    }

    .textarea-control {
        height: 85px;
    }

    .contact-form .button-container {
        text-align: center;
    }

    .contact-form .submit {
        padding: 16px 0;
        width: 100%;
        max-width: 200px;
        font-size: 16px;
        background-color: black;
        border-radius: 5px;
        color: whitesmoke;
        cursor: pointer;
        transition-duration: .3s;
        border: 2px solid rgba(255, 255, 255, .3);
        margin: 20px 0 60px;
    }

    .contact-form .submit:hover {
        background-color: #A42327;
        box-shadow: 0 0 10px 2px #a42327;
    }

    .loader {
        height: 13px;
        width: 13px;
        border: 3px solid #BBBBBB;
        border-bottom: 3px solid #A42327;
        border-radius: 50%;
        animation-name: rotate;
        animation-duration: 100s;
        animation-iteration-count: infinite;
        animation-timing-function: linear;
        display: none;
        margin: auto;
    }

    .loader-container {
        width: 44.45px;
    }

    .send-message {
        background-color: black;
        margin-top: 10px;
        color: white;
        border: 2px solid red;
        display: none;
        font-size: 16px;
    }
</style>