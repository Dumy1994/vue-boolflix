<template>
  <main>
    <div class="input-group mt-5 mb-3 barInput">
        <input @keyup.enter="searchButton" type="text" class="form-control" placeholder="Search" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="inputText">
        <button @click="searchButton" class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
        
    </div>
    <ol>
        <li v-for="(film, index) in search" :key="index">
            <h3>  Titolo: {{film.title}}</h3>
            <h3> Titolo Originale: {{film.original_title}}</h3>
            <h3>  Lingua: {{film.original_language}}</h3>
            <h3>  Voto: {{film.vote_average}}</h3>
        </li>
    </ol>
  </main>
</template>

<script>
import axios from 'axios';

export default {
    name:'AppMain',
    data(){
        return{
            inputText: '',
            apiPath:'https://api.themoviedb.org/3/search/',
            apiKey:'?api_key==e99307154c6dfb0b4750f6603256716d',
            search:[],
            index: [],
            compApi: {
                params:{
                    api_key: this.apiKey,
                    query: this.inputText,
                    language: 'it-IT'
                }
            }
        }
    },
    methods:{
        searchButton(){
            // const compApi = {
            //     params:{
            //         api_key: this.apiKey;
            //         query: this.inputText;
            //         language: 'it-IT'
            //     }
            // }
            axios.get(this.apiPath + 'movie' + this.compApi.params).then((res)=>{
            console.log(res.data.results)
            this.search = res.data.results
        })
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