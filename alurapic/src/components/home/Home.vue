<template>
    <div>
        <h1 class="centralizado">{{ titulo }}</h1>

        <input type="search" class="filtro" @input="filtro = $event.target.value" placeholder="Filtre por parte do título">

        <ul class="lista-fotos">
            <li class="lista-fotos-item" v-for="foto of fotosComFiltro">
                <meu-painel :titulo="foto.titulo">
                    <imagem-responsiva :url="foto.url" :titulo="foto.titulo"></imagem-responsiva>
                </meu-painel>
            </li>
        </ul>
    </div>
</template>

<script>

import Painel from "../shared/painel/Painel.vue";
import ImagemResponsiva from "../shared/imagem-responsiva/ImagemResponsiva.vue";

export default {

    components: {
        'meu-painel': Painel,
        'imagem-responsiva': ImagemResponsiva
    },

    data() {
        return {
            titulo: 'Alurapic',
            fotos: [],
            filtro: ''
        }
    },

    computed: {
        fotosComFiltro() {
            if(this.filtro){
                let exp = new RegExp(this.filtro.trim(), 'i');
                return this.fotos.filter(foto => exp.test(foto.titulo));
            } else {
                return this.fotos;
            }
        }
    },

    created() {
        let promise = this.$http.get('http://localhost:3000/v1/fotos')
        promise
            .then(res => res.json())
            .then(fotos => this.fotos = fotos, err => console.log(err))
    }

}
</script>

<style>

    .centralizado{
        text-align: center;
    }

    .lista-fotos{
        list-style: none;
    }

    .lista-fotos .lista-fotos-item{
        display: inline-block;
    }

    .filtro{
        display: block;
        width: 100%;
    }
</style>
