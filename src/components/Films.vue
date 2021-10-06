<template>

    <div class="wrapper">
        <h2>Movies</h2>

        <ul>
            <li v-for="(movie, index) in movies" :key="index"> 
                TITLE: {{movie.title}}
                ORIGINAL TITLE: {{movie.original_title}}
                LANG: {{movie.original_language}}
                VOTO: {{movie.vote_average}}
            </li>
        </ul>
    </div>
  
</template>

<script>

export default {
    name: 'Films',
    props:{
        movies: Array,
    },

}
</script>

<style>

</style>