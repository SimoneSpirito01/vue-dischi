<template>
    <div class="selects">
        <Select @search="getGenere" selectLabel="il genere" :array="generi"/>
        <Select @search="getArtista" selectLabel="l'artista" :array="artisti"/>
    </div>
</template>

<script>
import Select from '.././commons/Select.vue'

export default {
    name: 'Nav',
    components: {
        Select
    },
    props: {
        albums: Array
    },
    data(){
        return {
            genere: 'All',
            artista: 'All',
            generi: ['All'],
            artisti: ['All'],
        }
    },
    emits: {
        myEvent: null
    },
    methods: {
        getGenere: function(genere){
            this.genere = genere;
            this.$emit('search', this.genere, this.artista)
        },
        getArtista: function(artista){
            this.artista = artista;
            this.$emit('search', this.genere, this.artista)
        }
    },
    created(){
        this.albums.forEach(element => {
            if (!this.generi.includes(element.genre)) {
                this.generi.push(element.genre)
            }
        });
        this.albums.forEach(element => {
            if (!this.artisti.includes(element.author)) {
                this.artisti.push(element.author)
            }
        });
    }
}
</script>

<style lang="scss" scoped>

    .selects {
        height: 60px;
        display: flex;
        justify-content: center;
        align-items: center;

        > * {
            margin: 10px;
        }
    }

</style>