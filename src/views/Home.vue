<template>
    <div>
        <div class="containerMain">
            <h1>Faça seu Hambúrguer</h1>
        </div>
        <h1 class="make-burguer">Monte o seu Hambúrguer: </h1>
        <div class="formContainer">
            <form @submit="salvarPedido">
                <div class="container-input">
                    <label for="" class="titulo-label">Nome do Cliente:</label>
                    <input type="text" name="" id="" class="form-control" v-model="hamburguer.nomeCliente" required>
                </div>
                <div class="container-input">
                    <label for="" class="titulo-label" >Tipo de Pão:</label>
                    <select class="form-select" id="selectPao" v-model="hamburguer.pao" required>
                        <option selected disabled>Selecione uma opção</option>
                        <option value="Brioche">Brioche</option>
                        <option value="Tradicional">Tradicional</option>
                        <option value="Australiano">Australiano</option>
                        <option value="Integral">Integral</option>
                    </select>
                </div>
                <div class="container-input">
                    <label for="" class="titulo-label">Tipo de Carne:</label>
                    <select class="form-select" v-model="hamburguer.carne" required>
                        <option selected disabled>Selecione uma opção</option>
                        <option value="Bovina">Bovina</option>
                        <option value="Frango">Frango</option>
                        <option value="Porco">Porco</option>
                        <option value="Cordeiro">Cordeiro</option>
                    </select>
                </div>
                <div class="container-input">
                    <label for="" class="titulo-label">Selecione os adicionais:</label>
                    <div class="checkbox-container">
                        <div>
                            <input type="checkbox" v-model="hamburguer.adicionais" value="Salame">
                            <span>Salame</span>
                        </div>
                        <div>
                            <input type="checkbox" v-model="hamburguer.adicionais" value="Pepino">
                            <span>Pepino</span>
                        </div>
                    </div>
                    <div class="checkbox-container">
                        <div>
                            <input type="checkbox" v-model="hamburguer.adicionais" value="Queijo">
                            <span>Queijo</span>
                        </div>
                        <div>
                            <input type="checkbox" v-model="hamburguer.adicionais" value="Cebola">
                            <span>Cebola</span>
                        </div>
                    </div>
                    <div class="checkbox-container">
                        <div>
                            <input type="checkbox" v-model="hamburguer.adicionais" value="Alface"> 
                            <span>Alface</span>
                        </div>
                        <div>
                            <input type="checkbox" v-model="hamburguer.adicionais" value="Tomate"> 
                            <span>Tomate</span>
                        </div>
                    </div>
                </div>
                <button type="button" class="btn-form me-5" @click="salvarPedido"> Crie o seu hambúrguer!</button> 
                <div class="alert my-2" role="alert" v-bind:class="pedidoAceito(this.statusPedido)" v-show= mostrarAlerta>
                    {{ this.statusPedido ? "Pedido criado com sucesso" : "Faltam campos para serem preenchidos no pedido" }}
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Home',
    data(){
        return{
            hamburguer: {
                nomeCliente: "",
                pao: "Selecione uma opção",
                carne: "Selecione uma opção",
                adicionais: []
            },
            mostrarAlerta: false,
            statusPedido: false
        }
    },
    methods:{
        async salvarPedido(e){
            e.preventDefault();

            if(this.hamburguer.nomeCliente && this.hamburguer.pao && this.hamburguer.carne){
                const data = {
                    nomeCliente: this.hamburguer.nomeCliente,
                    pao: this.hamburguer.pao,
                    carne: this.hamburguer.carne,
                    adicionais: Array.from(this.hamburguer.adicionais)
                }

                const dataJson = JSON.stringify(data);

                const req = await fetch("https://jsonserver-rouge.vercel.app/hamburguer", {
                    method: "POST",
                    headers: {"Content-Type" : "application/json"},
                    body: dataJson
                })

                const res = await req.json();

                this.statusPedido = true;
            }

            this.hamburguer.nomeCliente = "";
            this.hamburguer.pao = "";
            this.hamburguer.carne = "";
            this.hamburguer.adicionais = [];

            this.mostrarAlerta = true;

            setTimeout(() => {
                this.mostrarAlerta = false;
                this.statusPedido = false;
            }, 2000);
        },

        pedidoAceito(status){
            return status == true ? 'alert-primary' : 'alert-warning';
        }
    }
}
import 'bootstrap/dist/css/bootstrap.css';
</script>

<style scoped>
    .containerMain{
        background-image: url('./../../public/imgs/burger.jpg');
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        height: 600px;
        display: flex;
        align-items: center;
    }

    .containerMain h1{
        padding-left: 40px;
        color: #ffffff;
        font-size: 50px;
        background-color: #222;
        padding: 20px;
    }

    .make-burguer{
        padding-top: 40px;
        text-align: center;
    }

    .formContainer{
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 30px;
    }

    .formContainer form{
        width: 300px;
        height: 580px;
    }

    .container-input{
        display: flex;
        flex-direction: column;
        margin-top: 20px;
    }

    .container-input .titulo-label{
        margin-bottom: 10px;
        font-weight: bold;
        border-left: #FCBA03 4px solid;
        padding-left: 10px;
    }

    .container-input input{
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        justify-content: space-between;
        margin-top: 10px;
    }

    .checkbox-container input{
        width: 20px;
    }

    

    .btn-form{
        width: 100%;
        margin-top: 10px;
        background-color: #222;
        color: #FCBA03;
        border: none;
        cursor: pointer;
        transition: 1s;
        height: 40px;
        font-weight: bold;
        border-radius: 5px;
    }

    .btn-form:hover{
        background-color:#FCBA03;
        color: #222;
    }

    @media screen and (max-width: 400px){
        .containerMain h1{
            width: 280px;
            font-size: 30px;
        }

        .formContainer form{
            width: 250px;
        }
    }
</style>