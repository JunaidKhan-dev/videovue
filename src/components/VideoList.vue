<template>
   <div id="video-list">

       <ul>
           <VideoListItem v-for='(item,index) in videosPass' :key="index">{{item}}</VideoListItem>

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
    }
}
</script>

<style scoped>

</style>
