<template>
    <section id="films">
        <h2 v-if='noMovies == true'>No movies found</h2>
        <h2 v-if='movies.length != 0'>MOVIES</h2>

        <div class="wrapper">
            <ul>
                <li v-for="(movie, index) in movies" :key="index">
                    <Card :api="movie"/>
                </li>
            </ul>
        </div> 
    </section>
</template>

<script>
import Card from './Card.vue';


export default {
    name: 'Films',
    props:{
        movies: Array,
        noMovies: Boolean
    },
    components:{
        Card,
    },

}


</script>

<style lang='scss' scoped>
@import '../assets/style/variables.scss';


#films{
    color: $primaryWhite;
    padding-top: 4.375rem;
    
    h2{
        margin: .9375rem 3.125rem;
        font-size: 3em;
        
    }

    li{
        width: 21.875rem;  
        
    }

}



</style>