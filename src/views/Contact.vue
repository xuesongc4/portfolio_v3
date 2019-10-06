<template>
    <section id="contact">
        <div class="container">
            <div class="contact-form">
                <div class="page_title">
                    Connect With Me
                </div>
                <div class="contact-form-container">
                    <img src="../assets/me_cartoon.png">
                    <form>
                        <input type="text" name="name" class="form-control" placeholder="Enter Your Name*">
                        <input type="email" name="email" class="form-control" placeholder="Enter Your Email*">
                        <textarea name="body" rows='4' cols="25" type="text" class="form-control textarea-control"
                                  placeholder="Enter Your Message*"></textarea>
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
    </section>
</template>

<script>
    export default {
        name: "Contact"
    }
</script>

<style scoped>
    #contact {
        background: url("../assets/stars2.png") center center no-repeat;
        position: relative;
    }

    .contact-form-container{
        width: 50%;
        margin: auto;
    }

    .contact-form{
        max-width: 1000px;
        width: 100%;
        border: 5px solid #A42327;
        border-radius: 20px;
        background-color: rgba(0,0,0,.5);
        position: absolute;
        top: 30%;
        left: 50%;
        transform: translate(-50%, -30%);
        font-size: 20px;
        box-shadow: 0 0 50px 5px black;
    }

    .contact-form .page_title{
        font-size: 50px;
        font-weight: 700;
        color: white;
    }

    .contact-form img{
        height: 150px;
        width: auto;
        border-radius: 50%;
        border: 5px solid #A42327;
        background-color: white;
        background-color: rgba(255,255,255,.7);
        display: block;
        margin: 40px auto;
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

    .form-control:focus{
        border: 2px solid #A42327;
        outline-width: 0;
    }

    ::-webkit-placeholder, ::-o-placeholder, ::-moz-placeholder {
        font-family: 'Montserrat', sans-serif;
        color: #d9d9d9;
        font-size: 15px;
    }

    .textarea-control{
        height: 85px;
    }

    .contact-form .button-container{
        text-align: center;
    }

    .contact-form .submit{
        padding: 16px 0;
        width: 100%;
        max-width: 200px;
        font-size: 16px;
        background-color: black;
        border-radius: 5px;
        color: whitesmoke;
        cursor: pointer;
        transition-duration: .3s;
        border: 2px solid rgba(255,255,255,.3);
        margin: 20px 0 60px;
    }

    .contact-form .submit:hover {
        background-color: #A42327;
    }

    .loader{
        height: 13px;
        width: 13px;
        border:3px solid #BBBBBB;
        border-bottom:3px solid #A42327;
        border-radius: 50%;
        animation-name: rotate;
        animation-duration: 100s;
        animation-iteration-count: infinite;
        animation-timing-function: linear;
        display: none;
        margin: auto;
    }
    .loader-container{
        width: 44.45px;
    }
    .send-message{
        background-color: black;
        margin-top: 10px;
        color: white;
        border: 2px solid red;
        display: none;
        font-size: 16px;
    }
</style>