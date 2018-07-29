<template>
    <div id="video-detail" v-if="video" class="col-lg-8">
        <div class="embed-responsive embed-responsive-16by9"> 
            <iframe  :src="videoUrl" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen class="embed-responsive-item"></iframe>
        </div>
        <div class="details">
             <h4>{{video.snippet.title}}</h4>
             <p>{{video.snippet.description}}</p>
        </div>
       
    </div>
</template>

<script>
export default {
    name:'VideoDetails',
    props:['video'],
    computed:{
        videoUrl(){
            const videoId = this.video.id.videoId
            return 'http://youtube.com/embed/' + videoId
        }
    }
}
</script>

<style scoped>
.details{
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;

}


</style>

