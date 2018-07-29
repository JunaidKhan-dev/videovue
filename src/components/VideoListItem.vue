<template>
    <div id="video-list-item">
        <li class="list-group-item media" @click="onVideoSelect">
            <img :src="url" alt="video thumbnail" class="mr-3">
            <div class="media-body">
                {{item.snippet.title}}
            </div>
            
        </li>
    </div>
</template>

<script>
export default {
    name:'VideoListItem',

    computed:{
        url(){
            return this.item.snippet.thumbnails.default.url
        }
    },
    props:['item'],
    methods:{
        onVideoSelect(e){
            
            this.$emit('videoSelect', this.item )
        }
    }
}
</script>

<style scoped>
#video-list-item li{
    display: flex;
    cursor: pointer;
}

#video-list-item li:hover{
    background-color: #eee;
}

</style>

