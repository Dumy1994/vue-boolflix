<template>
  <div class = "spinner" style = "font-size: 18px">
  <div class = "head"></div>
</div>
</template>

<script>
export default {
    name:'AppLoader',
    
    data(){
        return{
           
        }
    }
}
</script>

<style>

.spinner {
  width: 10em;
  height: 10em;
  border-top: 1em solid #6da9f5;
  border-right: 1em solid transparent;
  border-radius: 50%;
  margin: auto;
  animation: spinner 0.6s linear infinite;
}
.head {
  width: 1em;
  height: 1em;
  background-color: #6da9f5;
  border-radius: 50%;
  margin-left: 8.5em;
  margin-top: 0.5em;
}
@keyframes spinner {
  100% { transform: rotate(360deg) }
}


</style>