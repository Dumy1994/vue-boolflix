<template>
  <div class="row container-random">
      <h1 class="text-center">Top movie</h1>
        <div class=" card col-3" v-for="(img, index) in randomFilm" :key="index">
            <img class="" :src="'https://image.tmdb.org/t/p/w342/' + img.backdrop_path" alt=" ">
            <div class="info  text-center">
            <h3>
               {{img.title}}
            </h3>
            
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
.card{
   margin: 0 !important;
   padding: 0 !important;
   cursor: pointer;
}
.card:hover .info{
    display: block;

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