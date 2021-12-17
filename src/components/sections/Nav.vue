<template>
    <div class="selects">
        <Select @search="getGenere; $emit('search', genere )" :albums="albums"/>
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
            genere: ''
        }
    },
    emits: {
        myEvent: null
    },
    methods: {
        getGenere: function(genere){
            this.genere = genere;
            this.$emit('search', genere)
        }
    }
}
</script>

<style lang="scss" scoped>

    .selects {
        text-align: center;
    }

</style>