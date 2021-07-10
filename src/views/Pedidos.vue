<template> 
    <div class="pattern-pedido ">
        <Dashboard class="pattern-filtro" />
    </div>      
</template>

<script>
import Dashboard from '../components/Dashboard.vue'

    export default {
        name:"Pedidos",
        components: {
          Dashboard
        }
    }
</script>

<style scoped>    
    .pattern-pedido {   
      color: rgb(240, 172, 84);        
      position: relative;                 
      /* adicionando imagem de fundo */
      background-color: #000;
      background-image: url('/img/banner_pedido.jpg');
      background-size: cover;
      display: flex;  
      min-height: 100vh;
      height: auto;
      background-position: 0 -85px;
      padding: 0px 0px;  
      background-position: center;
      background-repeat: no-repeat;         
      /*filter: brightness(60%);*/
      /*opacity: 95%;*/

      /*
      <div class="pattern-pedido ">
        <Dashboard class="pattern-filtro" />
      </div>     

      <div class="main-container">
      <h1>Gerenciar pedidos:</h1>       
        <Dashboard />       
      </div>  
      */

    }    
    .pattern-filtro {
        background: rgba(0, 3, 12, 0.8);         
        padding: 0px;
        border-left: 0; 
        height: 80vh;    
        height: auto;      
        width: 100%;       
    }

</style>

