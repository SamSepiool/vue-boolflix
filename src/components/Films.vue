<template>

    <div class="wrapper">
        <h2>Movies</h2>

        <ul>
            <li v-for="(movie, index) in movies" :key="index"> 

                <img v-if="movie.poster_path != null" :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="">
                
                TITLE: {{movie.title}}
                ORIGINAL TITLE: {{movie.original_title}}
                LANG: {{movie.original_language}}
                <lang-flag :iso="movie.original_language" :squared="false"/>
                VOTO: {{movie.vote_average}}
                <font-awesome-icon v-for="(solid, index) in starsVote(movies)[index]" :key="index"   :icon='starSolid'/>
                <font-awesome-icon v-for="(empty, index) in (5 - starsVote(movies)[index])" :key="`ciccio`+index"   :icon='starEmpty'/>

            </li>
        </ul>
    </div>
  
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import { faStar as fasStar } from '@fortawesome/free-solid-svg-icons';
import { faStar as farStar } from '@fortawesome/free-regular-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
    name: 'Films',
    props:{
        movies: Array,
    },
    components:{
        LangFlag,
        FontAwesomeIcon
    },
    data(){
        return {
            starSolid: fasStar,
            starEmpty: farStar,

        }
    },
    methods:{
        
       starsVote(arr){
           const stars = [];
           arr.forEach((elm) => {

               let parseInStars = Math.ceil(elm.vote_average / 2);
               stars.push(parseInStars);
               
           })
           return stars;
       }

        
    }

}
</script>

<style>

</style>