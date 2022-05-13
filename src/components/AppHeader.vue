<template>
  <div class="container head-container ">
    <div class="row align-items-center ">
      <div class="col-6">
        <a href=""><h1>BOOLFLIX</h1></a>
      </div>
      <div class="col-6 input-button d-flex justify-content-end">
        <h4 class="">Cerca film o serie</h4>
        <input type="text" placeholder="Search" v-model="search" @keyup.enter="cerca">
        <button @click="cerca">Cerca</button>
      </div>
      
    </div>
  </div>
    
</template>

<script>

export default {
  components: { },
    name:'AppHeader',
    data(){
        return{
          search:'',
        }
    },
    methods:{
      cerca(){
            this.$emit('performSearch',this.search)
            this.search = ''
        }
    },
    computed:{
     
    },
    mounted(){

    }
}
</script>

<style lang="scss" scoped>
@import './style/variable.scss';

.head-container{
 
  .input-button{
    height: 30px;
  }
button{
  border: 0;
  border-left: 1px solid grey;
  padding-left: 5px;
  padding-right: 5px;
}
  input{
    border: 0;
  }
  h4{
    margin-right: 15px;
  }
  a{
    text-decoration: none;
    color: rgb(178, 22, 22);
  }
}




</style>