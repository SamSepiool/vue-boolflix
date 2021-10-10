<template>
    <section id="series">
        <h2 v-if='noSeries == true'>No series found</h2>
        <h2 v-if='tvSeries.length != 0'>SERIES</h2>

        <div class="wrapper"> 
            <ul >
                <li v-for="(serie, index) in tvSeries" :key="index">
                    <Card :api="serie"/>
                </li>
            </ul>    
        </div>
    </section>
</template>

<script>
import Card from './Card.vue'


export default {
    name: 'Series',
    props:{
        tvSeries: Array,
        noSeries: Boolean
    },
    components:{
        Card,
    },
}
</script>

<style lang='scss' scoped>
@import '../assets/style/variables.scss';

#series{
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