<template>
    <div class="about">
        <h1 class="title">Gerenciar Pedidos: </h1>
        <div class="table-wrapper">
            <table class="my-5">
                <thead>
                    <tr>
                        <th>ID:</th>
                        <th>Cliente:</th>
                        <th>Pão:</th>
                        <th>Carne:</th>
                        <th>Opcionais:</th>
                        <th>Ações:</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="pedidos in hamburguers" :key="pedidos.id">
                        <td>{{ pedidos.id }}</td>
                        <td>{{ pedidos.nomeCliente }}</td>
                        <td>{{ pedidos.pao }}</td>
                        <td>{{ pedidos.carne }}</td>
                        <td class="lista-opcionais">
                            <ul>
                                <li v-for="(adicional, index) in pedidos.adicionais" :key="index">
                                    {{ adicional }}
                                </li>
                            </ul>
                        </td>
                        <td class="td-inputs">
                            <select class="select-status">
                                <option value="">Pedido Aceito</option>
                                <option value="">Em Produção</option>
                                <option value="">Saiu Para Entrega</option>
                                <option value="">Pedido Entregue</option>
                            </select>
                            <button class="btn-cancelar">Cancelar</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: 'About',
    data(){
        return{
            hamburguers: []
        }
    },
    methods: {
        async buscarPedidos(){
            const req = await fetch("http://localhost:3000/hamburguer");
            const data = await req.json();
            this.hamburguers = data;
            console.log(this.hamburguers)
        }
    },
    mounted(){
        this.buscarPedidos();
    },
}
</script>

<style scoped>

    .about{
        min-height: 600px;
    }
    .title{
        padding-top: 40px;
        text-align: center;
        font-size: 50px;
    }


    .lista-opcionais{
        font-size: 14px;
    }

    .table-wrapper {
        overflow-x: auto; 
    }

    th, td {
        text-align: left;
        padding: 8px;
        white-space: nowrap;
    }

    tr{
        border-bottom: 1px solid #222;
    }

    thead{
        border-bottom: 3px solid #222;
    }

    table {
        border-collapse: collapse;
        width: 80%;
        margin: 20px auto;
        margin-top: 50px;
    }

    ul{
        margin: 0px;
        padding-left: 16px;
    }

    .select-status{
        height: 40px;
        width: 45%;
    }

    .btn-cancelar{
        height: 40px;
        width: 45%;
        background-color: #222;
        color: #FCBA03;
        cursor: pointer;
        transition: 1s;
        border: none;
        border-radius: 5px;
        font-weight: bold;
    }

    .btn-cancelar:hover{
        background-color: #FCBA03;
        color: #222;
    }

    .td-inputs{
        display: flex;
        justify-content: space-between;
    }

    @media screen and (max-width: 696px) {
        th, td {
            display: block; 
            width: 100%; 
        }

        tr{
            margin-top: 20px;
        }

        .td-inputs {
            flex-direction: column; 
        }

        .btn-cancelar, .select-status {
            width: 100%; 
            margin-top: 10px; 
        }
    }

</style>