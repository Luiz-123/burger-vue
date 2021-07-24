<template>
    <div id="burger-table">
        <Message :msg="msg" v-show="msg" />
        <div>
            <div id="burger-table-heading">
                <div class="order-id">#</div>
                <div>Cliente</div>
                <div>Pão</div>
                <div>Carne</div>
                <div>Opcionais</div>
                <div>Ações</div>
            </div>
        </div>

        <div id="burger-table-rows">

            <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                <div class="order-number">{{ burger.id }}</div>
                <div>{{ burger.nome }}</div>
                <div>{{ burger.pao }}</div>
                <div>{{ burger.carne }}</div>
                <div>
                    <ul>
                        <li v-for="(opcional,index) in burger.opcionais" :key="index">
                            {{ opcional }}
                        </li>
                        
                    </ul>
                </div>
                <div>
                    <select name="status" class="status" @change="updatedBurger($event, burger.id)">                        
                        <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">
                            {{ s.tipo }}
                        </option>
                    </select>
                    <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import Message from './Message.vue'

    export default {
        name:"Dashboard",
        data() {
            return {
                burgers: null,
                burger_id: null,
                status: [],
                msg: null
            }
        },
        components: {
            Message
        },
        methods: {
            async getPedidos() {
                const req = await fetch("http://localhost:3000/burgers");
                const data = await req.json();
                this.burgers = data;

                //Resgatar os status
                this.getStatus();
            },
            async getStatus() {
                const req = await fetch("http://localhost:3000/status");
                const data = await req.json();
                this.status = data;
            },
            async deleteBurger(id) {
                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "DELETE"
                });
                const res = await req.json();

                //Colocar uma mensagem de sistema
                this.msg = `Pedido cancelado com sucesso!`;

                //Limpar a mensagem de sistema
                setTimeout(() => this.msg = "", 3000);

                this.getPedidos();
            },
            async updatedBurger(event, id) {
                const option = event.target.value;
                const dataJson = JSON.stringify({ status:option });
                const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                    method: "PATCH",
                    headers: {"Content-Type":"Application/json"},
                    body: dataJson
                });
                const res = await req.json();

                //Colocar uma mensagem de sistema
                this.msg = `Pedido Nº ${res.id}: Atualizado para ${res.status}.`;

                //Limpar a mensagem de sistema
                setTimeout(() => this.msg = "", 3000);
                
                //console.log(res);
            }
        },
        mounted() {
            this.getPedidos();
        }
    }
</script>

<style scoped>
    #burger-table {
        max-width: 1200px;
        margin: 0 auto;
    }
    #burger-table-heading,
    #burger-table-rows,
    .burger-table-row {
        display: flex;
        flex-wrap: wrap;
    }
    #burger-table-heading {
        font-weight: bold;
        padding: 10px;
        border-bottom: 2px solid #fff;
        color: #fff;
    }
    #burger-table-heading div,
    .burger-table-row div {
        width: 19%;
    }
    .burger-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #ccc;
    }
    #burger-table-heading .order-id,
    .burger-table-row .order-number {
        width: 5%;
    }
    select {
        padding: 9px 1px;
        margin-right: 5px;
        background-color: transparent;
        color: rgb(156, 167, 15); /* rgb(143, 101, 47); rgb(179, 125, 55); */
        border: 2px solid rgb(178, 189, 25); /*rgb(109, 109, 108); rgb(29, 175, 243); rgb(131, 203, 236); rgb(144, 224, 128); rgb(228, 146, 40);*/
        border-radius: 5px;
        width: 90px;
        cursor: pointer;
    }    
    .delete-btn {
        background-color: transparent;
        color: rgb(253, 253, 246);
        font-weight: bold;
        border: 2px solid rgb(253, 253, 246); /*rgb(220, 233, 38);*/
        border-radius: 5px;
        padding: 10px;
        font-size: 12px;
        margin: 0 auto;
        margin-left: 5px;
        cursor: pointer;
        transition: .4s;               
    }
    .delete-btn:hover {
        background-color: transparent;
        color: rgb(226, 4, 4);
        border: 2px solid rgb(226, 4, 4);  
        /*rgb(226, 4, 4);rgb(233, 10, 10);rgb(218, 25, 185);*/      
    }    
</style>
