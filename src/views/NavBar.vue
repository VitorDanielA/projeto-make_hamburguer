<template>
    <div class="nav">
        <img :src="img" :alt="alt">
        <router-link to="/" class="link">Fazer Pedido</router-link>
        <router-link to="/about" class="link">Pedidos</router-link>
    </div>
</template>

<script>
export default {
    name: 'NavBar',
    data(){
        return{
            img: './../../imgs/logo.png',
            alt: 'Hamburger'
        }
    }
}
</script>

<style scoped>
    .nav{
        background-color: #222;
        display: flex;
        align-items: center;
        justify-content: flex-end;
        padding: 10px 40px;
        border-bottom: 4px solid #000;
    }

    .nav img{
        margin: auto;
        margin-left: 0px;
        height: 60px;
    }

    .link{
        color: #FCBA03;
        text-decoration: none;
        margin-right: 40px;
        transition: .5s;
    }

    .link:hover{
        color: #fff;
    }

    @media screen and (max-width: 400px){
        .nav{
            padding: 10px  5px;
        }
    }

    @media screen and (max-width: 280px){
        .nav img{
            padding-right: 20px;
        }
    }
</style>