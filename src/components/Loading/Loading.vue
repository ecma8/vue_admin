<template>
    <div class="loading">
        <div class="loader-inner ball-scale-multiple">
            <div></div>
            <div></div>
            <div></div>
        </div>
    </div>
</template>
<style lang="scss">
    @-webkit-keyframes ball-scale-multiple {
        0% {
            -webkit-transform: scale(0);
            transform: scale(0);
            opacity: 0;
        }

        10% {
            opacity: 1;
        }

        100% {
            -webkit-transform: scale(1);
            transform: scale(1);
            opacity: 0;
        }
    }

    @keyframes ball-scale-multiple {
        0% {
            -webkit-transform: scale(0);
            transform: scale(0);
            opacity: 0;
        }

        10% {
            opacity: 1;
        }

        100% {
            -webkit-transform: scale(1);
            transform: scale(1);
            opacity: 0;
        }
    }

    .ball-scale-multiple {
        position: relative;
        -webkit-transform: translateY(-30px);
        -ms-transform: translateY(-30px);
        transform: translateY(-30px); }
    .ball-scale-multiple > div:nth-child(2) {
        -webkit-animation-delay: 0.2s;
        animation-delay: 0.2s;
    }
    .ball-scale-multiple > div:nth-child(3) {
        -webkit-animation-delay: 0.4s;
        animation-delay: 0.4s;
    }
    .ball-scale-multiple > div {
        background-color: #4f9dff;
        border-radius: 100%;
        -webkit-animation-fill-mode: both;
        animation-fill-mode: both;
        position: absolute;
        left: 0;
        top: 0;
        opacity: 0;
        margin: 0;
        width: 100px;
        height: 100px;
        -webkit-animation: ball-scale-multiple 1s 0s linear infinite;
        animation: ball-scale-multiple 1s 0s linear infinite;
    }
    .loading{
        width: 60%;
        height: 60%;
        background: #fff;
        position: fixed;
        left:0;
        top:0;
        right: 0;
        bottom: 0;
        margin: auto;
        z-index: 10000000000;
        text-align: center;
        perspective:120px;
        transition: all 1s ease;
    }

    .loading .ball-scale-multiple{
        position: absolute;
        left:0;
        top:0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 100px;
        height: 100px;
    }
</style>
<script>
    export default {

    }
</script>