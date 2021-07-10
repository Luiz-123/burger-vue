<template>
    <div id="main-banner">
        <!-- <h1>Make Your Burger</h1> -->
    </div>
</template>

<script>
    export default {
        name:"Banner"
    }
</script>

<style scoped>
    #main-banner {
        background-image: url('/img/banner_home.jpg');
        background-position: 0 -5px;
        background-size: cover;
        height: 450px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        filter: brightness(40%);
    }

    #main-banner h1 {
        color: #fff;
        text-align: center;
        font-size: 45px;
        background-color: #222;
        padding: 20px 40px;
        background: transparent;        
    }
</style>
