<template>
    <div class="card">
        <img v-if="api.poster_path != null " :src="`https://image.tmdb.org/t/p/w342/${api.poster_path || api.poster_path}`" alt="">

        
        <ul class="info">
            <li>Title: {{api.title || api.name}}</li>

            <li>Original title: {{api.original_title || api.original_name}}</li>

            <li>Original language: <lang-flag :iso="api.original_language || api.original_language" :squared="false"/></li>

            <li>Vote: 
                <font-awesome-icon v-for="(solid, index) in starsVote(api)" :key="index"   :icon='starSolid'/>
                <font-awesome-icon v-for="(empty, index) in (5 - starsVote(api))" :key="`other`+index"   :icon='starEmpty'/>
            </li>

            <li v-if="api.overview || api.overview != '' " >Overview: <p>{{api.overview || api.overview}}</p></li>

        </ul>
    </div>
  
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import { faStar as fasStar } from '@fortawesome/free-solid-svg-icons';
import { faStar as farStar } from '@fortawesome/free-regular-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
    name: 'Card',
    props:{
        api: Object, 
    },
    components:{
        LangFlag,
        FontAwesomeIcon
        
    },
    data(){
        return{
            starSolid: fasStar,
            starEmpty: farStar,
        }
    },
    methods:{

        starsVote(obj){
        return Math.ceil(obj.vote_average / 2)
       }

    }

}
</script>


<style>

</style>