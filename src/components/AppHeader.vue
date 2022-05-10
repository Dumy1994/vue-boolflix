<template>
  <div>
    <header-search/>
  </div>
</template>

<script>
import HeaderSearch from './HeaderSearch.vue'
export default {
  components: { HeaderSearch },
    name:'AppHeader',
    data(){
        return{

        }
    },
    methods:{

    },
    computed:{

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