<template>
    <div id="app">
        <SearchBar @termChanges='onTermChange'></SearchBar>
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'

const API_KEY = 'AIzaSyAF4nx7XAZE21ThK9Fb9a0bNQeDvNIJ0vQ'

export default {
    name:'App',
    components:{
        SearchBar
    },
    methods:{
        onTermChange(SearchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params:{
                    key: API_KEY, //API key 
                    type: 'video', //Which type of search we need
                    part:'snippet', //which part we want to recive back (snippet means small info)
                    q:SearchTerm //query is equal to the search term from input by user


                }
            }).then(res=>{
                console.log(res)
            })

        }
    }
}
</script>
<style scoped>

</style>
