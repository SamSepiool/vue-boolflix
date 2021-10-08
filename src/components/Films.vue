<template>
    <section class="films">
        <h2 v-if='movies.length == 0'>No result</h2>
        <h2 v-if='movies.length != 0'>Movies</h2>

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
    },
    components:{
        Card,
    },
}


</script>

<style lang='scss' scoped>
@import '../assets/style/variables.scss';


.films{
    background-color: $primaryBlack;
    color: $primaryWhite;
    padding-top: 4.375rem;
    
    h2{
    padding: .9375rem;

    }

}

</style>