<template>
  <div>
      <div class="input-group mt-5 mb-3 barInput">
            <input @keyup.enter="searchButton" type="text" class="form-control" placeholder="Search" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="inputText">
            <button @click="searchButton" class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
            
       </div>
  </div>
</template>

<script>
export default {
    name:'HeaderSearch',
    props: ['template'],
    data(){
        return{
            inputText: '',
        }
    },
    methods:{
        
    }

}
</script>

<style>

</style>