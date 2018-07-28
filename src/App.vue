<template>
    <div id="app">
        <SearchBar @termChanges='onTermChange'></SearchBar>
        <VideoList :videosPass='videos'></VideoList>
        
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'



export default {
    name:'App',
    data(){
        return{
            videos:[]
        }
    },
    components:{
        SearchBar,
        VideoList
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
                this.videos = res.data.items
                console.log(this.videos)
            })

        }
    }
}
</script>
<style scoped>

</style>
