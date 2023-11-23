<template>
    <div>
        <h1>{{ titulo }}</h1>
        <img :src="foto.url" :alt="foto.titulo">
    </div>
</template>

<script>
export default {
    data() {
        return {
            titulo: 'Alurapic',
            foto: {
                url: 'https://img.freepik.com/fotos-gratis/cao-feliz-sorridente-isolado-fundo-branco-retrato-2_1562-691.jpg',
                titulo: 'Cachorro'
            }
        }
    }

}
</script>

<style>

</style>
