<template>
    <div class="album-card">
        <div class="image">
            <img :src="album.poster" :alt="album.title">
        </div>
        <div class="text">
            <h3>{{album.title}}</h3>
            <p>{{album.author}}</p>
            <p>{{album.year}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AlbumCard',
    props: {
        album: Object
    }
}
</script>

<style lang="scss" scoped>

    .album-card {
        background-color: #2e3a46;
        text-align: center;
        padding: 15px;
        height: 100%;
        cursor: pointer;
        transition: transform 0.8s;

        &:hover {
            transform: scale(1.05);
        }

        img {
            width: 90%;
        }

        h3 {
            font-size: 20px;
            color: white;
            text-transform: uppercase;
            margin: 20px 0 10px;
        }

        p {
            color: #808080;
            margin: 0;
        }
    }

</style>