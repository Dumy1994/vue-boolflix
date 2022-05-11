<template>
    <section>
        <h2>{{title}}</h2>
       <ul>
        <li v-for="(item) in items" :key="item.id">
          id: {{item.id}}<br />
          titolo originale: {{item.original_title ? item.original_title : item.original_name}}<br />
          titolo: {{item.title ? item.title : item.name}}<br />
          lingua: {{item.original_language}}<br />
         
          voto: {{item.vote_average}}<br />
        </li>
      </ul>
     
    </section>
</template>

<script>
//import {state, actions} from '../store.js'
export default {
    name: 'GridList',
    props:['items','title'],
    data(){
        return {
            
        }
    },
    computed: {
        // mysearch(){
        //     return state.search
        // }
    },
    methods:{
        // leggi(){
        //     actions.setSearch('aaaaa')
        // }
    }
}
</script>

<style lang="scss">

</style>