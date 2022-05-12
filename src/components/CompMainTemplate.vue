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
                <div>
                    Lingua: 
                    <img class="flag" v-if="flags.includes(item.original_language)" :src="require(`../assets/${item.original_language}.jpg`)" :alt="item.original_language">
                    <span v-esle>
                        {{item.original_language}}
                    </span>
                </div>
                
                Voto: 
                <span v-for="(i,index) in 5" :key="index">
                    <i :class="i <= transformScale(item) ? 'fa-solid gold fa-star' : 'fa-regular fa-star'"></i>
                </span>
              
            </div>
            
            </li>
        </ul>
    </section>
</template>

<script>

export default {
    name: 'GridList',
    props:{
        items: Array,
        // loader: Boolean,
        title: String
    },
    data(){
        return {
            flags:['en', 'es','it']
        }
    },
    computed: {
        
    },
    methods:{
        transformScale(item){
            return parseInt(item.vote_average / 2) 
        },
        
        
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
    .gold{
        color: rgb(224, 224, 15);
    }
</style>