<template>
  <main class="container">
   <app-header @performSearch="search" />
    
    <comp-main-template :items="movies" title="Movies" />
    <comp-main-template :items="series" title="Series" />
  </main>
</template>

<script>
import axios from 'axios';
import CompMainTemplate from './CompMainTemplate.vue';
import AppHeader from './AppHeader.vue';

export default {
  components: { CompMainTemplate, AppHeader },
    name:'AppMain',
    data(){
        return{
            inputText: '',
            apiPath:'https://api.themoviedb.org/3/search/',
            apiKey:'e99307154c6dfb0b4750f6603256716d',
            movies:[],
            series: [],
        }
    },
    methods:{
    getMovies(queryParams){
      axios.get(this.apiPath + 'movie', queryParams).then((res)=>{
        this.movies = res.data.results;
        // this.loading = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    getSeries(queryParams){
      axios.get(this.apiPath + 'tv', queryParams).then((res)=>{
        this.series = res.data.results;
        // this.loadingSeries = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    search(text){
       const queryParams = {
        params:{
          api_key: this.apiKey,
          query: text,
        }
      }
    //   this.loading = true;
    //   this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    }
  },
    computed:{

    },
    mounted(){
        
    }
}
</script>

<style lang="scss" >
@import "./style/general.scss";

.barInput{
    width: 30vw;
    
}

</style>