<template>
   <div id="video-list" class="col-8 offset-2 justify-content-center">
       
       <ul class="list-group" >
            <transition-group name="list" tag="p">
                 <VideoListItem v-for='item in videosPass' :key="item.etag" :item='item' 
           @videoSelect="onVideo"></VideoListItem>
            </transition-group>
          

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

.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}

</style>
