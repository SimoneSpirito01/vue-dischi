<template>
    <main class="d-flex justify-content-center align-items-center">
        <div class="my_container" v-if="albums != null">
            <Nav :albums="albums" @search="getGenere"/>
            <div class="row row-cols-5 gx-4 justify-content-center">
                <div class="col" v-for="(album, i) in albumsFiltered" :key="i">
                    <AlbumCard :album="album"/>
                </div>
            </div>
        </div>
        <div v-else>
            <Loader/>
        </div>
    </main>
</template>

<script>
import AlbumCard from './commons/AlbumCard.vue';
import Loader from './commons/Loader.vue';
import Nav from './sections/Nav.vue';

export default {
    name: 'Main',
    components: {
        AlbumCard,
        Loader,
        Nav
    },
    data() {
        return {
            albums: null,
            genere: ''
        }
    },
    methods: {
        getGenere: function(genere){
            this.genere = genere
        }
    },
    created() {
        console.log(this.genere)
        const self = this;

        // setTimeout(() => {
            const axios = require('axios');

            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(function (response) {
                self.albums = response.data.response;
            })
            .catch(function (error) {
                console.log(error);
            })
        // }, 1000);
    },
    computed: {
        albumsFiltered(){
            if (this.genere == 'All'){
                return this.albums;
            } else {
                const arrayFiltered = this.albums.filter(element => {
                    return element.genre.toLowerCase().includes(this.genere.toLowerCase());
                });
                return arrayFiltered;
            }
            
        }
    }
}
</script>

<style lang="scss" scoped>

    main {
        height: calc(100vh - 65px);
        background-color: #1e2d3b;

        .my_container {
            width: 70%;
            max-width: 1200px;
            height: 95%;
            max-height: 800px;

            .row {
                height: 100%;
                align-content: center;

                .col {
                    height: 45%;
                    margin: 10px 0;
                }
            }
        }
        
    }

</style>