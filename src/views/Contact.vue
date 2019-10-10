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
                        <form @submit="onSubmit" action="POST" data-netlify="true">
                            <div class="input-row">
                                <div class="input-container">
                                    <input type="text" name="name" :maxlength="maxChar" class="form-control"
                                           v-model="form.value.name" :class="{ 'error': form.error.name === 'error'}"
                                           placeholder="Name*">
                                    <div class="errorMessage" v-if="form.errorMessage.name">{{form.errorMessage.name}}
                                    </div>
                                </div>
                                <div class="input-container">
                                    <input type="email" name="email" :maxlength="maxChar" class="form-control"
                                           v-model="form.value.email" :class="{ 'error': form.error.email === 'error'}"
                                           placeholder="Email*">
                                    <div class="errorMessage" v-if="form.errorMessage.email">
                                        {{form.errorMessage.email}}
                                    </div>
                                </div>
                            </div>
                            <div class="textarea-container">
                                 <textarea name="body" rows='4' cols="25" type="text" :maxlength="maxChar"
                                           class="form-control textarea-control" v-model="form.value.message"
                                           :class="{'error': form.error.message === 'error'}"
                                           placeholder="Message*"></textarea>
                                <div class="errorMessage" v-if="form.errorMessage.message">
                                    {{form.errorMessage.message}}</div>
                            </div>
                            <div class="button-container">
                                <button class="submit" type="submit" name="submit">
                                    <div class="send">
                                        SEND
                                    </div>
                                    <div class="loader-container">
                                        <div class="loader"></div>
                                    </div>
                                </button>
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
        name: "Contact",
        data() {
            return {
                form: {
                    value: {
                        email: "",
                        name: "",
                        message: ""
                    },
                    error: {
                        email: null,
                        name: null,
                        message: null
                    },
                    errorMessage: {
                        email: "",
                        name: "",
                        message: ""
                    },
                    ready: false
                },
                maxChar: 255
            }
        },
        methods: {
            onSubmit($event) {
                $event.preventDefault();
                this.form.errorMessage.name = "";
                this.form.errorMessage.email = "";
                this.form.errorMessage.message = "";

                if (this.form.value.message && this.form.value.name && this.form.value.email) {
                    this.form.ready = true;
                } else {
                    if (!this.form.value.name) {
                        this.form.errorMessage.name = "Please enter your name";
                        this.form.error.name = "error";
                    }
                    if (!this.form.value.email) {
                        this.form.errorMessage.email = "Please enter your email address"
                        this.form.error.email = "error";
                    }
                    if (!this.form.value.message) {
                        this.form.errorMessage.message = "Please enter a message"
                        this.form.error.message = "error";
                    }
                }
            }
        }
    }
</script>

<style scoped>
    .error {
        border-left: 5px solid red !important;
    }

    .map-bg {
        background: url("../assets/map.png") center center no-repeat;
        background-size: cover;
        height: 100vh;
        width: 100vw;
        z-index: -100;
        position: fixed;
        bottom: 0;
    }

    .stars-bg {
        background: url("../assets/stars-bg2.png") no-repeat;
        background-position-x: center;
        background-position-y: -60px;
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
        position: relative;
        flex: 1 1 0;
        width: 100%;
        margin: 10px 0;
    }
    .input-container:first-of-type{
        margin-right: 20px;
    }
    .textarea-container{
         position: relative;
         width: 100%;
         margin: 10px 0;
    }

    .input-row {
        display: flex;
    }

    .input-row input, .textarea-container textarea {
        border: 3px solid transparent;
        box-sizing:border-box;
        padding: 8px 12px;
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
        border-radius: 5px;
        color: black;
        font-size: 16px;
        width: 100%;
    }

    .form-control:focus {
        border: 2px solid #A42327;
        outline-width: 0;
        box-shadow: 0 0 10px 1px #A42327;
    }

    ::placeholder {
        color: dimgray;
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

    .errorMessage {
        text-align: left;
        color: lightcoral;
        font-size: 16px;
        background-color: rgba(255,255,255,.1);
        padding: 8px 6px;
        line-height: 20px;
        top: -4px;
        position: relative;
    }
</style>