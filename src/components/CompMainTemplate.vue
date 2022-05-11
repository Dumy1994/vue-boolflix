<template>
    <section class="container-fluid">
        
        <h2>{{title}}</h2>
        <ul class="row justify-content-center">
            
            <li class="card col-3" v-for="(item) in items" :key="item.id">
            <img class="img-film" :src="'https://image.tmdb.org/t/p/w342/' + item.backdrop_path" alt="">
            <div class="info">
                <!-- id: {{item.id}}<br /> -->
                Titolo originale: {{item.original_title ? item.original_title : item.original_name}}<br />
                Titolo: {{item.title ? item.title : item.name}}<br />
                Lingua: <img class="flag" :src="(item.original_language !== 'it') ? item.original_language : require('../assets/' + item.original_language + '.jpg') " >
                Voto: {{item.vote_average}}<br/>
            </div>
            
            </li>
        </ul>
    </section>
</template>

<script>
//import {state, actions} from '../store.js'
export default {
    name: 'GridList',
    props:['items','title'],
    data(){
        return {
            
        }
    },
    computed: {
        // mysearch(){
        //     return state.search
        // }
    },
    methods:{
        // leggi(){
        //     actions.setSearch('aaaaa')
        // }
    }
}
</script>

<style lang="scss">
    .flag{
        height: 10px;
        width: 10px;
    }
    ul{
        padding-left: 0 !important;
        padding-right: 0!important;
        li{
           margin: 10px ;
           width: calc((100vw / 3) - 20px) !important;
           .img-film{
            
            
           }
        }
    }
</style>