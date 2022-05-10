<template>
  <main>
    <div class="input-group mt-5 mb-3">
        <input @keyup.enter="searchButton" type="text" class="form-control" placeholder="Search" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="inputText">
        <button @click="searchButton" class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
    </div>
  </main>
</template>

<script>
export default {
    name:'AppMain',
    data(){
        return{
            inputText: '',
            apiPath:'https://api.themoviedb.org/3/search/',
            api_key:'=e99307154c6dfb0b4750f6603256716d',
            search:'',
        }
    },
    methods:{
        searchButton(){
            console.log(this.inputText)
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


</style>