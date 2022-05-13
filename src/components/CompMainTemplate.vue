<template>
    <section class="container-fluid">
        
        
        <div class="title text-center">
             <h2>{{title}}</h2>
        </div>
        <!-- <div class="row " v-if="show = show">
            <div class=" col-4" v-for="(img, index) in randomFilm" :key="index">
                 <img class="" :src="'https://image.tmdb.org/t/p/w342/' + img.backdrop_path" alt=" ">
            </div>
        </div> -->
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
                <!-- info  -->
                <!-- <div @click="openCloseInfo(item)"  class="info-film-button">
                    <h3>Info</h3>
                </div>
                <div v-if="info_film == item.id" class="review-film">
                    <div class="review">
                        <h3 class="text-center">
                            Info <br>
                            {{item.overview ? item.overview : 'Sorry this content isnt available at the moment'}}
                        </h3>
                    </div>
                </div> -->
                
                </li>
            </ul>
       </div>
    </section>
</template>
<script>
import axios from 'axios';
export default {
    name: 'GridList',
    props:{
        items: Array,
        
        // loader: Boolean,
        title: String
    },
    data(){
        return {
            flags:['en', 'es','it'],
            info_film: '',
            review_film: '',
            img: 'https://image.tmdb.org/t/p/w342/',
            mainPage: true,
            randomFilm:'',
            
        }
    },
    
    
    methods:{
        
        
        transformScale(item){
            return parseInt(item.vote_average / 2) 
        },
        // openCloseInfo(item){
        //     if(this.info_film.length == 0){
        //         return this.info_film = item.id;
        //     }else{
        //         return this.info_film = ''
        //     }
        // },
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
    mounted(){
        axios.get('https://api.themoviedb.org/3/trending/movie/day?api_key=e99307154c6dfb0b4750f6603256716d').then((res)=>{
                this.randomFilm = res.data.results;
                console.log(this.randomFilm)
                })
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
    
    .review-film-button{
        position: absolute;
        left: 0;
        top: 0;
        background-color:$white-text;
        z-index: 10000;
        color: $bg-text-card;
        cursor: pointer;
        padding: 5px;
        border-bottom-right-radius: 10px;
    }
    // .info-film-button{
    //     position: absolute;
    //     right:  0;
    //     top: 0;
    //     background-color:$white-text;
    //     z-index: 10000;
    //     color: $bg-text-card;
    //     cursor: pointer;
    //     padding: 5px;
    //     border-bottom-left-radius: 10px;
    // }
    .review-film{
        position: absolute;
        top: 0;
        background-color:$bg-text-card;
        color: white;
        height: 100%;
        width: 100%;
        overflow: scroll;
        h3{
            margin-top: 30px;
        }
    }

</style>