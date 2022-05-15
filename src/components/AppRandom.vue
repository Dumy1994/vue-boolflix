<template>
  <div class="main-page">
      <h1 class="text-center m-5">Top movie</h1>
      <div class="d-flex container-random">
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
      <!-- series top  -->
      <h1 class="text-center m-5">Top series</h1>
      <div class="d-flex container-random">
        <div class=" card col-3" v-for="(serie, index) in randomSeries" :key="index">
            <img class="" :src="'https://image.tmdb.org/t/p/w342/' + serie.backdrop_path" alt=" ">
            <div class="info  text-center">
            <h2>
               {{serie.title}}

            </h2>
            <h5>Voto: {{transformScale(serie)}}</h5>
            <span  v-for="(i,index) in 5" :key="index">
                <i :class="i <= transformScale(serie) ? 'fa-solid gold fa-star' : 'fa-regular fa-star'"></i>
            </span>
            
            </div>  
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
            randomSeries:'',
           
        }
    },
    methods:{
        transformScale(img){
            return parseInt(img.vote_average / 2) 
        },
        transform(serie){
            return parseInt(serie.vote_average / 2) 
        },
    },
    mounted(){
        axios.get('https://api.themoviedb.org/3/trending/movie/day?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT').then((res)=>{
                this.randomFilm = res.data.results;
                console.log(this.randomFilm)
                });
         axios.get('https://api.themoviedb.org/3/trending/tv/day?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT').then((res)=>{
                this.randomSeries = res.data.results;
                console.log(this.randomSeries)
                })
    },
    filters: {
        
    }
}
</script>

<style lang="scss" scoped>

.container-random{
   width: 100vw;
   overflow: auto;
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


@media only screen and (max-width: 576px) {
 .text-center{
     display: none;
 }
 .card{
     margin-top: 50px !important;
 }
  
}
</style>