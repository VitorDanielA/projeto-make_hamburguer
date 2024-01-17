<template>
    <div>
        <div>
            <table class="table table-dark my-3 container">
                <thead>
                    <tr>
                        <th scope="col">User ID</th>
                        <th scope="col">ID</th>
                        <th scope="col">Título</th>
                        <th scope="col">Concluído</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in dadosPaginas" :key="item.id">
                        <td scope="row">{{item.userId}}</td>
                        <td scope="row">{{item.id ? item.id : item.identificação}}</td>
                        <td scope="row">{{item.title ? item.title : item.título}}</td>
                        <td scope="row">{{item.concluído}}</td>
                    </tr>
                </tbody>
            </table>
            <nav class="container d-flex justify-content-center" aria-label="Navegação">
                <ul class="pagination">
                    <li class="page-item" @click="getPaginaAnterior()"><a class="page-link" href="#">Anterior</a></li>
                    <li v-for="paginas in totalPaginas()" :key="paginas" class="page-item" @click="getDataPaginas(paginas)" v-bind:class="isActive(paginas)"><a class="page-link" href="#">{{paginas}}</a></li>
                    <li class="page-item" @click="getPaginaSeguinte()"><a class="page-link" href="#">Próximo</a></li>
                </ul>
            </nav>
        </div>
    </div>
</template>

<script>

import { lista } from './../Data.js';

export default {
    name: 'paginacao',
    data(){
        return{
            lista: lista,
            elementosPorPagina: 10,
            dadosPaginas: [],
            pagAtual: 1
        }
    },
    mounted(){
        this.getDataPaginas(1);
    },
    methods: {
         totalPaginas(){
            return Math.ceil(this.lista.length / this.elementosPorPagina)
         },
         getDataPaginas(pagAtual){
            this.pagAtual = pagAtual;
            this.dadosPaginas = [];
            let numIni = (pagAtual * this.elementosPorPagina) - this.elementosPorPagina;
            let numFinal = (pagAtual * this.elementosPorPagina);

            this.dadosPaginas = this.lista.slice(numIni, numFinal);
         },
         getPaginaAnterior(){
            if(this.pagAtual > 1){
                this.pagAtual--;
            }
            this.getDataPaginas(this.pagAtual);
         },
         getPaginaSeguinte(){
            if(this.pagAtual < this.totalPaginas()){
                this.pagAtual++;
            }
            this.getDataPaginas(this.pagAtual);
         },
         isActive(pag){
            return pag == this.pagAtual ? 'active' : ''
         }   
    },
}
</script>