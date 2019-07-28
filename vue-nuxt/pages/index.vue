<template>
    <div class="container">
        <h1 class="title">{{titulo}}</h1>
         <div class="columns is-multiline">
            <!-- <SummonerCard :summoner="summoner" v-for="summoner in summoners" :key="summoner.id"></SummonerCard> -->
            <AlbumCard :album="album" v-for="album in albums" :key="album.id"></AlbumCard>
         </div>
    </div>
</template>

<script>
import axios from 'axios';
import env from '../config/env';
import AlbumCard from '../components/AlbumCard';
// import SummonerCard from '../components/SummonerCard';
export default {
    name: 'IndexPage',
    components:{
        // SummonerCard,
        AlbumCard,
    },                            
    data() {
        return {
            albums:[],
            titulo:"Lista de albums",
        }
    },
    
    created(){
        // axios.get(`${env.champions}`).then(response =>{
        //     console.log(response);
        //     this.summoners=response.data.data;
        //     console.log("summoners",this.summoners["Aatrox"].image.full);
        //     this.image="https://ddragon.leagueoflegends.com/cdn/9.14.1/img/champion/";
        // }); 
        axios.get(`${env.endpoint}albums`).then(response =>{
            this.albums=response.data;
            console.log("albums",this.albums);
        
        }); 
    }
}
</script>
