<template>

    <div class="wrapper">
        <h2>Movies</h2>
        <ul>
            <li v-for="(movie, index) in movies" :key="index">
                <Card :api="movie"/>
            </li>
        </ul>
    </div> 
  
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

<style>

</style>