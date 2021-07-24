<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
        <h1><img :src="logo" :alt="alt" id="logo"> Make Your Burger</h1>       
    </router-link>      
    <router-link to="/">Home</router-link> |
    <router-link to="/pedidos">Pedidos</router-link>
  </div>    
</template>

<script>
    export default {
        name: "Navbar",
        props: ["logo","alt"]
    }
</script>

<style scoped>
    #nav {
        background-color: rgb(242, 247, 241);
        border-bottom: 2px solid #111;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center; 
    }

    #nav #logo-url {
        margin: auto;
        margin-left: 0;
    }

    #nav h1 {
        margin-top: 10px;   
        margin-bottom: 0px;         
    }

    #logo {
        width: 40px;
        height: 40px;
    }

    #nav a {
        color: rgb(56, 33, 2);
        text-decoration: none;
        margin: 12px;
        transition: .5s;
    }

    #nav a:hover {
        color: rgb(139, 82, 8); /*rgb(173, 35, 35);*/
    }
</style>
