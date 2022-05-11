<template>
  <div id="app">
    <header>
     <app-header @performSearch="search" />
    </header>
   <main>
    <comp-main-template :items="movies" title="Movies" />
    <comp-main-template :items="series" title="Series" />
   </main>
  </div>
</template>

<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import CompMainTemplate from './components/CompMainTemplate.vue';

export default {
  name: 'App',
  components: {CompMainTemplate,AppHeader  },

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

<style lang="scss">
@import "./components/style/general.scss";
main{
  width: 100vw;
}
</style>
