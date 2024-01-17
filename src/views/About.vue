<template>
    <div class="about">
        <h1 class="title">Gerenciar Pedidos: </h1>
        <div class="table-wrapper">
            <table>
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
                    <tr>
                        <td>1</td>
                        <td>Madson</td>
                        <td>Australiano</td>
                        <td>Bovina</td>
                        <td class="lista-opcionais">
                            <ul>
                                <li>Salame</li>
                                <li>Alface</li>
                            </ul>
                        </td>
                        <td class="td-inputs">
                            <select name="" id="" class="select-status">
                                <option value="">Pedido Aceito</option>
                                <option value="">Em Produção</option>
                                <option value="">Saiu Para Entrega</option>
                                <option value="">Pedido Entregue</option>
                            </select>
                            <button class="btn-cancelar">Cancelar</button>
                        </td>
                    </tr>
                    <tr>
                        <td>2</td>
                        <td>Raul</td>
                        <td>Integral</td>
                        <td>Frango</td>
                        <td class="lista-opcionais">
                            <ul>
                                <li>Pepino</li>
                                <li>Queijo</li>
                            </ul>
                        </td>
                        <td class="td-inputs">
                            <select name="" id="" class="select-status">
                                <option value="">Pedido Aceito</option>
                                <option value="">Em Produção</option>
                                <option value="">Saiu Para Entrega</option>
                                <option value="">Pedido Entregue</option>
                            </select>
                            <button class="btn-cancelar">Cancelar</button>
                        </td>
                    </tr>
                    <tr>
                        <td>3</td>
                        <td>João</td>
                        <td>Brioche</td>
                        <td>Porco</td>
                        <td class="lista-opcionais">
                            <ul>
                                <li>Cebola</li>
                                <li>Tomate</li>
                            </ul>
                        </td>
                        <td class="td-inputs">
                            <select name="" id="" class="select-status">
                                <option value="">Pedido Aceito</option>
                                <option value="">Em Produção</option>
                                <option value="">Saiu Para Entrega</option>
                                <option value="">Pedido Entregue</option>
                            </select>
                            <button class="btn-cancelar">Cancelar</button>
                        </td>
                    </tr>
                    <tr>
                        <td>4</td>
                        <td>Vitor</td>
                        <td>Tradicional</td>
                        <td>Cordeiro</td>
                        <td class="lista-opcionais">
                            <ul>
                                <li>Salame</li>
                                <li>Queijo</li>
                            </ul>
                        </td>
                        <td class="td-inputs">
                            <select name="" id="" class="select-status">
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
}
</script>

<style scoped>
    .title{
        padding-top: 40px;
        text-align: center;
        font-size: 50px;
    }

    table {
        border-collapse: collapse;
        width: 80%;
        margin: 20px auto;
        margin-top: 50px;
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

    .lista-opcionais{
        padding-left: 25px;
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