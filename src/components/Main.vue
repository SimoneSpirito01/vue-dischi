<template>
    <main class="d-flex justify-content-center align-items-center">
        <div class="my_container" v-if="albums != null">
            <div class="row row-cols-5 gx-4">
                <div class="col" v-for="(album, i) in albums" :key="i">
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
import AlbumCard from './commons/AlbumCard.vue'
import Loader from './commons/Loader.vue'

export default {
    name: 'Main',
    components: {
        AlbumCard,
        Loader
    },
    data() {
        return {
            albums: null
        }
    },
    created() {
        const self = this;

        setTimeout(() => {
            const axios = require('axios');

            console.log()

            // Make a request for a user with a given ID
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(function (response) {
                // handle success
                self.albums = response.data.response;
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
        }, 1000);
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