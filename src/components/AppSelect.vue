<template>
  <div >
      <select  name="type" id="type" v-model="inputText" @change="changeType">
          <option  value="">all</option>
          <option  :value="type" v-for="(type, index) in genType" :key="index">{{type}}</option>
      </select>
  </div>
</template>

<script>

export default {
    name:'AppSelect',
    data(){
        return{
            inputText: '',
        }
    },
    props:['genType'],
    methods:{
        changeType(){
            this.$emit("performSearch", this.inputText);
            
        }
    }
    
}
</script>

<style lang="scss">
select{
    position: absolute;
    top: 5vh;
    
}


</style>