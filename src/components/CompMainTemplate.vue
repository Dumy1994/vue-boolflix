<template>
    <div class=" row ">
        <div class="card ">
            <h3>  Titolo: {{title}}</h3>
            <h3> Titolo Originale: {{original_title}}</h3>
            <h3>  Lingua: {{original_language}}</h3>
            <h3>  Voto: {{vote_average}}</h3>
        </div>
    </div>
</template>

<script>
export default {
    name:'CompMainTemplate',
    props: ['original_language','vote_average','original_title','title'],
}
</script>

<style>

</style>