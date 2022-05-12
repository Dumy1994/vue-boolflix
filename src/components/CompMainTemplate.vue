<template>
    <section class="container-fluid">
        <div class="title">
             <h2>{{title}}</h2>
        </div>
       <div class="grid">
           <ul class="row  justify-content-center">
            
                <li class="card img-film p-0 col-3" v-for="(item) in items" :key="item.id">
                <img class="" :src="'https://image.tmdb.org/t/p/w342/' + item.backdrop_path" :alt="item.original_title ">
                <div class="info">
                    
                    <div class="title-movie">
                        <h3 v-if="item.original_title  == item.title">
                            Original title: {{item.original_title ? item.original_title : item.original_name}} 
                        </h3>
                        <h3 v-if="item.original_title !== item.title">
                            Italian title: {{item.title ? item.title : item.name}} <br>
                            Original title: {{item.original_title ? item.original_title : item.original_name}} 
                        </h3>
                    </div>
                    
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
                <div class="ghost text-center">
                    <h3>Review</h3>
                    <h3>
                        {{item.overview ? item.overview : 'Not available at the moment, we apologize.'}}
                    </h3>
                </div>
                
                </li>
            </ul>
       </div>
        
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
    @import './style/variable.scss';

    .flag{
        height: 15px;
        
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
    .ghost{
        position: absolute;
        left: 0;
        background-color:$bg_card;
        color: $white-text;
        height:230px ;
        width: 100%;
        overflow: scroll;
        border-radius: 2px;
        display: none;
        cursor: pointer;
    }
    .img-film:hover .ghost{
        display: block;
    }

</style>