<template>
    <div>
        <h1>{{ titulo }}</h1>

        <ul>
            <li v-for="foto of fotos">
                <img :src="foto.url" :alt="foto.titulo">
            </li>
        </ul>

    </div>
</template>

<script>
export default {
    data() {
        return {
            titulo: 'Alurapic',
            fotos: [
                {
                    url: 'https://img.freepik.com/fotos-gratis/cao-feliz-sorridente-isolado-fundo-branco-retrato-2_1562-691.jpg',
                    titulo: 'Golden'
                },
                {
                    url: 'https://blog.cobasi.com.br/wp-content/uploads/2020/07/boston-terrier-capa1.png',
                    titulo: 'Pug'
                }
            ]
        }
    }

}
</script>

<style>

</style>
