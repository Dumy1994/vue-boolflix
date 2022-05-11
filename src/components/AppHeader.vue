<template>
     <div>
      <input type="text" v-model="search" @keyup.enter="$emit('performSearch',search)">
      <button @click="cerca">Cerca</button>
    </div>
</template>

<script>
// import state from '../store.js'
export default {
  components: { },
    name:'AppHeader',
    data(){
        return{
          search:'' 
        }
    },
    methods:{
      cerca(){
            this.$emit('performSearch',this.search)
            this.search = ''
        }
    },
    computed:{
      // mysearch(){
      //   return state.search
      // }
    },
    mounted(){

    }
}
</script>

<style lang="scss" scoped>
@import "./style/general.scss";

div{
  height: 10vh;
}


</style>