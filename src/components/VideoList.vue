<template>
   <div id="video-list" class="col-lg-4">

       <ul class="list-group">
           <VideoListItem v-for='item in videosPass' :key="item.etag" :item='item' 
           @videoSelect="onVideo"></VideoListItem>

       </ul>
       </div> 
</template>

<script>
import VideoListItem from './VideoListItem'
export default {
    name:'VideoList',
    props:[
        'videosPass'
    ],
    components:{
       VideoListItem 
    },
    methods:{
        onVideo(videoSelect){
            this.$emit('videoEmit', videoSelect)

        }
    }
}
</script>

<style scoped>

</style>
