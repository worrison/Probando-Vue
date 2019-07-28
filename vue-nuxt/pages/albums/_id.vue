<template>
    <div>
        <h1>{{album.title}}</h1>
        <div class="column"  v-for="photo in photos" :key="photo.id">
            <img :src="photo.url" :alt="photo.title" />
        </div>
         
    </div>
</template>

<script>
import router from 'vue-router';
import axios from 'axios';
import env from '../../config/env';
export default {
    name:'AlbumIndvPage',

    data(){
        return{
            album: {},
            photos: [],
        }
    },

    created: async function()
    {
        let responseAlbum = await axios.get(`${env.endpoint}albums/${this.$route.params.id}`);
        this.album=responseAlbum.data; 

        let responsePhotos= await axios.get(`${env.endpoint}albums/${this.$route.params.id}/photos`);
        this.photos=responsePhotos.data;
        console.log("photos",this.photos);
    }
}
</script>
