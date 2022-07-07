<template>
    <section class="container-fluid pt-3">
       <div class="grid">
           
           <ul class="row  justify-content-center align-items-center justify-content-center">
                <li class="card cardCercato   img-film p-0 col-sm-4 col-md-3 col-lg-3" v-for="(item) in items" :key="item.id">
                    <div class="filmImg" >
                        <img :src="'https://image.tmdb.org/t/p/w342/' + item.poster_path" :alt="item.original_title ">
                    </div>
                
                <div class="info p-1">
                    <div class="title-movie">
                        
                        
                        <h3 class="color-title-original" v-if="item.original_title  == item.title">
                            Original title: {{item.original_title ? item.original_title : item.original_name}} 
                        </h3>
                        <h3 v-if="item.original_title !== item.title">
                            <h3 class="color-title-original">
                            Original title: {{item.original_title ? item.original_title : item.original_name}} 
                            </h3> 
                            Italian title: {{item.title ? item.title : item.name}} <br>
                            
                        </h3>
                    </div>
                    <!-- lingua  -->
                    <div >
                        Lingua originale: 
                        <img class="flag" v-if="flags.includes(item.original_language)" :src="require(`../assets/${item.original_language}.png`)" :alt="item.original_language">
                        <span v-esle>
                            {{item.original_language}}
                        </span>
                        
                    </div >
                    <!-- genere  -->
                    <div v-for="(gen, index) in genres" :key="index">
                        <span>
                            {{gen.id == item.genre_ids[0] ? gen.name : ''}}
                        </span>
                    </div>
                    <!-- voto  -->
                    Voto: 
                    <div class="d-flex "  >
                        <span v-for="(i,index) in 5" :key="index" >
                            <i :class="i <= transformScale(item) ? 'fa-solid gold fa-star' : 'fa-regular fa-star'"></i>
                        </span>
                    </div>

                    <h3 class=" voto">{{title}}</h3>
                </div>
                <!-- review  -->
                <div @click="openClose(item)"  class="review-film-button">
                    <h3>Review</h3>
                </div>
                
                <div v-if="review_film == item.id" class="review-film">
                      <div class="review">
                        <h3 class="text-center">
                            Review <br>
                            {{item.overview ? item.overview : 'Sorry this content isnt available at the moment'}}
                        </h3>
                    </div>
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

        title: String
    },
    data(){
        return {
            flags:['en', 'es','it','ja','fr'],
            
            info_film: '',
            review_film: '',
            img: 'https://image.tmdb.org/t/p/w342/',
            mainPage: true,
            genres: [ { id: 28, name: "Action" }, { id: 12, name: "Adventure" }, { id: 16, name: "Animation" }, 
            { id: 35, name: "Comedy" }, { id: 80, name: "Crime" }, { id: 99, name: "Documentary" }, { id: 18, name: "Drama" }, { id: 10751, name: "Family" }, { id: 14, name: "Fantasy" }, { id: 36, name: "History" }, { id: 27, name: "Horror" }, { id: 10402, name: "Music" }, { id: 9648, name: "Mystery" }, { id: 10749, name: "Romance" }, { id: 878, name: "Science Fiction" }, { id: 10770, name: "TV Movie" }, { id: 53, name: "Thriller" }, { id: 10752, name: "War" }, { id: 37, name: "Western" }
             ]
        }
    },
    
    
    methods:{
        
        showRandom(items){
            if(items == ''){
                return !this.show
            }
        },
        
        transformScale(item){
            return parseInt(item.vote_average / 2) 
        },

        openClose(item){
            if(this.review_film.length == 0){
                return this.review_film = item.id;
            }else{
                return this.review_film = ''
            }
        },
          
    },
    computed: {
        
    },
    
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
        }
    }
    .gold{
        color: rgb(224, 224, 15);
    }
    
    
    .review-film-button{
        position: absolute;
        right: 0;
        top: 0;
        background-color:$white-text;
        z-index: 10000;
        color: $bg-text-card;
        cursor: pointer;
        padding: 5px;
        border-bottom-left-radius: 10px;
        border-left: 1px solid black;
        border-bottom: 1px solid black;
    }
    
    .review-film{
        position: absolute;
        top: 0;
        background-color:$bg-text-card;
        color: white;
        height: 100%;
        width: 100%;
        overflow: scroll;
        border-radius: 5px;
        h3{
            margin-top: 30px;
        }
    }
    .info{
       
       display: none;
    }
    .voto{
       margin-right: 10px; 
    }
    .filmImg{
        height: 100%;
        object-fit: fill;
        img{
            width: 100%;
            border-top-left-radius: 5px;
            
        }
    }
    .color-title-original{
        color: $bg-text-card;
    }
    .cardCercato{
        min-height: 300px ;     
        overflow: hidden;
        &:hover .info{
            display: block;
            position: absolute;
            left: 0;
            background-color: $bg-header;
            height: 100%;
            display: flex;
            width: 100%;
            justify-content: center;
            align-items: center;
            flex-flow: column;  
            cursor: pointer;
        } 
     }



</style>