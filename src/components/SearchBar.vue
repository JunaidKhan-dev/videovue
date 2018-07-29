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
#search-bar{
    text-align: center;
    margin: 20px;
}
#search-bar input{
    width:75%;


}


</style>

