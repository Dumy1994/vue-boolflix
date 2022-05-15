<template>
  <div id="app">
    <header>
     <app-header @performSearch="search" />
     
    </header>
   <main>
     <app-loader v-if="loading" />
     <app-random v-if="show"/>
    
    <comp-main-template :items="movies" title="Movie" />
    <comp-main-template :items="series" title="Serie" />
   </main>
  </div>
</template>

<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import CompMainTemplate from './components/CompMainTemplate.vue';
import AppLoader from './components/AppLoader.vue';
import AppRandom from './components/AppRandom.vue';

export default {
  name: 'App',
  components: {CompMainTemplate,AppHeader, AppLoader, AppRandom  },

      data(){
        return{
          inputText: '',
            apiPath:'https://api.themoviedb.org/3/search/',
            apiKey:'e99307154c6dfb0b4750f6603256716d',
            movies:[],
            series: [],
            loading:false,
            show: true,
            
        }
  },
  methods:{
    getMovies(queryParams){
      axios.get(this.apiPath + 'movie', queryParams).then((res)=>{
        this.movies = res.data.results;
        this.loading = false;
        this.show = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    getSeries(queryParams){
      axios.get(this.apiPath + 'tv', queryParams).then((res)=>{
        this.series = res.data.results;
        
      }).catch((error)=>{
        console.log(error);
      })
    },
    search(text){
       const queryParams = {
        params:{
          api_key: this.apiKey,
          genres: '',
          language: 'it-IT',
          query: text,
          
        }
      }
      this.loading = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    }
  },
    computed:{

    },

    
}
</script>

<style lang="scss">
@import "./components/style/general.scss";
header{
  background-color: $bg-header;
  height: 7vh;
  position: fixed;
  left: 0;
  top: 0;
  width: 100vw;
  z-index: 100000000;
  color: $text-header;
}
main{
  margin-top: 7vh;
  width: 100vw;
  background-color: $bg-main;
  color: $grey-text;
}
</style>
