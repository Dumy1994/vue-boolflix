<template>
  <div class="row container-random">
      <h1 class="text-center">Top movie</h1>
        <div class=" card col-3" v-for="(img, index) in randomFilm" :key="index">
            <img class="" :src="'https://image.tmdb.org/t/p/w342/' + img.backdrop_path" alt=" ">
            <div class="info  text-center">
            <h2>
               {{img.title}}

            </h2>
            <h5>Voto: {{transformScale(img)}}</h5>
            <span  v-for="(i,index) in 5" :key="index">
                <i :class="i <= transformScale(img) ? 'fa-solid gold fa-star' : 'fa-regular fa-star'"></i>
            </span>
            
            </div>  
        </div>
          
        </div>
        
</template>

<script>
import axios from 'axios';

export default {
    name:'AppRandom',
    props:{
        
    },
    data(){
        return{
            randomFilm:'',
           
        }
    },
    methods:{
        transformScale(img){
            return parseInt(img.vote_average / 2) 
        },
    },
    mounted(){
        axios.get('https://api.themoviedb.org/3/trending/movie/day?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT').then((res)=>{
                this.randomFilm = res.data.results;
                console.log(this.randomFilm)
                })
    },
    filters: {
        
    }
}
</script>

<style lang="scss" scoped>
.container-random{
   width: 100vw;
}
.gold{
        color: rgb(224, 224, 15);
    }
.card{
   margin: 0 !important;
   padding: 0 !important;
   cursor: pointer;
}
.card:hover .info{
    display: block;
    cursor: pointer;

}
.info{
    position: absolute;
    left: 0;
    color: rgb(255, 255, 255);
    font-weight: 800;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.698);
    height: 100%;
    display: none;
}



</style>