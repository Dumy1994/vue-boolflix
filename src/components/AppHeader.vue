<template>
    <div class="d-flex justify-content-center align-items-center container-header">
      <div class="col-6">
        <h1>BOOLFLIX</h1>
      </div>
      <div class="col-6">
        <input type="text" v-model="search" @keyup.enter="$emit('performSearch',search)">
        <button @click="cerca">Cerca</button>
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
@import "./style/general.scss";

.container-header{
  height: 10vh;
  background-color: rgb(105, 88, 88);
}


</style>