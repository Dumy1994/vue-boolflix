<template>
    <section class="container-fluid pt-3">
       <div class="grid">
           <ul class="row  justify-content-center">
                <li class="card img-film p-0 col-3" v-for="(item) in items" :key="item.id">
                    <div class="filmImg" >
                        <img :src="'https://image.tmdb.org/t/p/w342/' + item.backdrop_path" :alt="item.original_title ">
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
                    <div >
                        Lingua originale: 
                        <img class="flag" v-if="flags.includes(item.original_language)" :src="require(`../assets/${item.original_language}.jpg`)" :alt="item.original_language">
                        <span v-esle>
                            {{item.original_language}}
                        </span>
                    </div >
                    Voto: 
                    <span  v-for="(i,index) in 5" :key="index">
                        <i :class="i <= transformScale(item) ? 'fa-solid gold fa-star' : 'fa-regular fa-star'"></i>
                    </span>
                    <h3 class="float-end voto">{{title}}</h3>
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
        border-radius: 5px;
        h3{
            margin-top: 30px;
        }
    }
    .title-movie{
        min-height: 100px;
        
    }
    .voto{
       margin-right: 10px; 
    }
    .filmImg{
        min-height: 50%;
        img{
            width: 100%;
            border-top-left-radius: 5px;
        }
    }
    .color-title-original{
        color: $bg-text-card;
    }
    .card{
        min-height: 400px;
    }

</style>