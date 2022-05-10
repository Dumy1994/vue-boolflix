<template>
  <div id="app">
    <header>
       <app-header/>
    </header>
   
    <app-main/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'


export default {
  name: 'App',
  components: {
    AppMain,
    AppHeader
  
  }
}
</script>

<style lang="scss">

</style>
