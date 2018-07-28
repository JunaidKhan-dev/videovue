<template>
    <div id="search-bar">
        <input type="text" @input="onInput">
    </div>
</template>

<script>
export default {
    name:'SearchBar',
    methods:{
        onInput(e){
            this.$emit('termChanges', e.target.value )
            

        }
    }
}
</script>

<style scoped>

</style>

