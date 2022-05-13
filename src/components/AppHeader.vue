<template>
  <div class="container head-container ">
    <div class="row align-items-center ">
      <div class="col-6">
        <h1>BOOLFLIX</h1>
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

}




</style>