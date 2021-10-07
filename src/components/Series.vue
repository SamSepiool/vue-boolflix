<template>

    <div class="wrapper">
        <h2>Series</h2>

        <ul>
            <li v-for="(series, index) in tvSeries" :key="index"> 
                <img v-if="series.poster_path != null" :src="`https://image.tmdb.org/t/p/w342/${series.poster_path}`" alt="">
               
                TITLE: {{series.name}}
                ORIGINAL TITLE: {{series.name}}
                LANG: {{series.original_language}}
                <lang-flag :iso="series.original_language" :squared="false"/>
                VOTO: {{series.vote_average}}
                <font-awesome-icon v-for="(solid, index) in starsVote(tvSeries)[index]" :key="index"   :icon='starSolid'/>
                <font-awesome-icon v-for="(empty, index) in (5 - starsVote(tvSeries)[index])" :key="`ciccio`+index"   :icon='starEmpty'/>
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
    name: 'Series',
    props:{
        tvSeries: Array,
    },
    components:{
        LangFlag,
        FontAwesomeIcon

    },
    data(){
        return {
            starSolid: fasStar,
            starEmpty: farStar,
            stars: [],
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

<style lang='scss' scoped>
.far{
    color:yellow;
    font-size: 50px;
}

</style>