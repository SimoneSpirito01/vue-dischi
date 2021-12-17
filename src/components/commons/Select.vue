<template>
    <div class="select">
        <label for="generi">Seleziona {{selectLabel}}:</label>
        <select v-model="selectValue" name="generi" id="generi" @change="$emit('search', selectValue)">
            <option v-for="(a, i) in array" :key="i" :value="a">
                {{a}}
            </option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Select',
    props: {
        selectLabel: String,
        array: Array

    },
    data(){
        return {
            
            selectValue: 'All'
        }
    },
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