<template>
    <div id="video-list-item">
        <div v-if="ready">
            
            <div>
                  <li class="list-group-item media" @click="onVideoSelect">
                    <img :src="url" alt="video thumbnail" class="mr-3">
                    <div class="media-body">
                        {{item.snippet.title}}
                    </div>
            
                </li>
            </div>
            
         

        </div>
        
    </div>
</template>

<script>
export default {
    name:'VideoListItem',
    data(){
        return{
            ready:true
        }
    },

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

