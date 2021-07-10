<template>
    <div id="burger-table">
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
                    <select name="status" class="status">
                        <option value="">Selecione</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
    export default {
        name:"Dashboard",
        data() {
            return {
                burgers: null,
                burger_id: null,
                status: []
            }
        },
        methods: {
            async getPedidos() {
                const req = await fetch("http://localhost:3000/burgers");
                const data = await req.json();
                this.burgers = data;

                //Resgatar os status
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
        color: rgb(253, 253, 246);
        border: 2px solid rgb(253, 253, 246);
        border-radius: 5px;
    }
    .delete-btn {
        background-color: transparent;
        color: rgb(220, 233, 38);
        font-weight: bold;
        border: 2px solid rgb(220, 233, 38);
        border-radius: 5px;
        padding: 10px;
        font-size: 12px;
        margin: 0 auto;
        margin-left: 5px;
        cursor: pointer;
        transition: .5s;               
    }
    .delete-btn:hover {
        background-color: transparent;
        color: rgb(226, 4, 4);   
        border: 2px solid rgb(226, 4, 4);  
        /*rgb(233, 10, 10);*/      
    }
</style>
