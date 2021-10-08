<template>
    <section class="series">
        <h2>Series</h2>
        <div class="wrapper">
            
            <ul>
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
    },
    components:{
        Card,
    },
}
</script>

<style lang='scss' scoped>
@import '../assets/style/variables.scss';

.series{
    color: $primaryWhite;
    padding-top: 4.375rem;
    
    h2{
        padding: .9375rem;
        font-size: 2em;
    }

    li{
        width: 20%;  
    }

}



</style>