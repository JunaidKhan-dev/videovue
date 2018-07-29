<template>
    <div id="app" class="container">
        <SearchBar @termChanges='onTermChange'></SearchBar>
        <div class="row">
            <VideoDetails :video="selectedVideoByUser"></VideoDetails>
            <VideoList :videosPass='videos' @videoEmit="onVideoSelectclick"></VideoList>
        </div>
        
        
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetails from './components/VideoDetails'

const API_KEY = 'AIzaSyAF4nx7XAZE21ThK9Fb9a0bNQeDvNIJ0vQ'

export default {
    name:'App',
    data(){
        return{
            videos:[],
            selectedVideoByUser:null,
        }
    },
    components:{
        SearchBar,
        VideoList,
        VideoDetails
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
                
            })

        },

        onVideoSelectclick(selectedVideo){
            this.selectedVideoByUser = selectedVideo

        }
    }
}
</script>
<style scoped>

</style>
