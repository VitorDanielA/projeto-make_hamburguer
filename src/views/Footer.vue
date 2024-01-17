<template>
    <footer>
        <p>{{ frase }} &copy;</p>
    </footer>
</template>

<script>
export default {
    name: 'Footer',
    data(){
        return{
            frase: '2024 Projeto para estudo'
        }
    }
}
</script>

<style scoped>
    footer{
        background-color: #222;
        color: #FCBA03;
        display: flex;
        align-items: center;
        justify-content: center;
        min-height: 180px;
    }

    @media screen and (max-width: 940px){
        footer{
            min-height: 280px;
        }
    }
</style>