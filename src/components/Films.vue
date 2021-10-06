<template>

    <div class="wrapper">
        <h2>Movies</h2>

        <ul>
            <li v-for="(movie, index) in movies" :key="index"> 
                TITLE: {{movie.title}}
                ORIGINAL TITLE: {{movie.original_title}}
                LANG: {{movie.original_language}}
                <lang-flag :iso="movie.original_language" :squared="false"/>
                VOTO: {{movie.vote_average}}
            </li>
        </ul>
    </div>
  
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'Films',
    props:{
        movies: Array,
    },
    components:{
        LangFlag
    }

}
</script>

<style>

</style>