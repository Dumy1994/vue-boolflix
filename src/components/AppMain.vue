<template>
  <main class="container">
    <div class="input-group mt-5 mb-3 barInput">
        <input @keyup.enter="searchButton" type="text" class="form-control" placeholder="Search" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="inputText">
        <button @click="searchButton" class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
        
    </div>
    
    <comp-main-template v-for="(film, index) in search" :key="index" :vote_average="film.vote_average" :original_language="film.original_language" :title="film.title" :original_title="film.original_title"/>
  </main>
</template>

<script>
import axios from 'axios';
import CompMainTemplate from './CompMainTemplate.vue';

export default {
  components: { CompMainTemplate },
    name:'AppMain',
    data(){
        return{
            inputText: '',
            apiPath:'https://api.themoviedb.org/3/search/',
            api_key:'=e99307154c6dfb0b4750f6603256716d',
            search:[],
            index: [],
            // compApi: {
            // params:{
            //     api_key: this.apiKey,
            //     query: this.inputText,
            //     language: 'it-IT'
            //     }
            // }
        }
    },
    methods:{
        searchButton(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT&query=' + this.inputText).then((res)=>{
            console.log(res.data.results)
            this.search = res.data.results
            })
        },
       
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