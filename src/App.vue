<template>
    <div id="app" class="fluid-container" v-cloak>
        <SearchBar @termChanges='onTermChange'></SearchBar>
        <div class="row">
           
            <VideoDetails :video="selectedVideoByUser" ></VideoDetails>
            <VideoList :videosPass='videos' @videoEmit="onVideoSelectclick" ></VideoList>
         
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
                    maxResults: '6',
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
            console.log(this.selectedVideoByUser)

        }
    },
    mounted(){
        
    }
}
</script>
<style>
body{
background: #b4e391; /* Old browsers */
background: -moz-linear-gradient(top, #b4e391 0%, #61c419 50%, #b4e391 100%); /* FF3.6-15 */
background: -webkit-linear-gradient(top, #b4e391 0%,#61c419 50%,#b4e391 100%); /* Chrome10-25,Safari5.1-6 */
background: linear-gradient(to bottom, #b4e391 0%,#61c419 50%,#b4e391 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
}

.header{

background-color:#00695C;
height: 100px;

}

#header-container  h1 span{
font-size: 20px;
}

.text-center a{
text-decoration: none;
color: white;
}

[v-cloak] {
    opacity: 0 !important;
}



</style>
