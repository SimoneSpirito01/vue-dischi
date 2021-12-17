<template>
    <div class="select">
        <label for="generi">Seleziona il genere:</label>
        <select v-model="selectValue" name="generi" id="generi" @change="$emit('search', selectValue)">
            <option v-for="(genere, i) in generi" :key="i" :value="genere">
                {{genere}}
            </option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Select',
    props: {
        albums: Array,
    },
    data(){
        return {
            
            generi: ['All'],
            selectValue: ''
        }
    },
    methods: {
       
    },
    created(){
        this.selectValue = this.generi[0];
        this.albums.forEach(element => {
            if (!this.generi.includes(element.genre)) {
                this.generi.push(element.genre)
            }
        });
    }
}
</script>

<style lang="scss" scoped>

    .select {

        label {
            color: white;
            margin-right: 10px;
        }
    }

</style>