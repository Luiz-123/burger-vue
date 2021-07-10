<template>
  <div id="main-banner">
        <!-- <h1>Make Your Burger</h1> -->
        <div class="pattern-pedido">
            <div class="pattern-filtro ">
                <p>  11111111</p>                
                <p>  0000000</p>
                <p>  0000000</p>
                <p>  0000000</p>
                <p>  2222222</p>
            </div>            
        </div>
  </div>

  
</template>

<script>
    export default {
        name:"Pedidos"
    }
</script>

<style scoped>    
    .pattern-pedido {   
      color: rgb(240, 172, 84);        
      position: relative;                 
      /* adicionando imagem de fundo */
      background-image: url('/img/banner_pedido8.jpg');
      background-size: cover;
      display: flex;  
      min-height: 90vh;
      height: auto;
      background-position: 0 -85px;
      padding: 30px 20px;  
      background-position: center;
      background-repeat: no-repeat;         
      /*filter: brightness(60%);*/
      /*opacity: 95%;*/
    }    

    .pattern-filtro {
        background: rgba(0, 3, 12, 0.8);         
        padding: 0px;
        border-left: 0; 
        height: 80vh;    
        height: auto;      
        width: 100%;       
    }

    .titulo-pedido {
      margin-top: 20px;
      margin-bottom: 20px;
      color: rgb(8, 68, 40);
      text-align: center;
      font-size: 38px;
    }
</style>

