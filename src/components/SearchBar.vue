<template>
    <div class="container col-8 offset-2">
        <div id="search-bar" class="">
            
            <label for="search" class="mr-3 text-light text">  <i  class="fab fa-youtube"></i> Youtube Search </label>
        <input type="text" @input="onInput" value="Vue Js" id="search">
    </div>
    </div>
    
</template>

<script>
export default {
    name:'SearchBar',
    methods:{
        onInput(e){
            
           setTimeout(()=>{
               this.$emit('termChanges', e.target.value )
           },1000)
            
            

        }
    },
    mounted(){
        let value = 'Vue vs react'
        this.$emit('termChanges', value )
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

.text{
    font-size: 30px;
}

</style>

