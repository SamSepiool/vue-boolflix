<template>

    <div class="wrapper">
        <h2>Series</h2>
        <ul>
            <li v-for="(serie, index) in tvSeries" :key="index">
                <Card :api="serie"/>
            </li>
        </ul>    
    </div>
  
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


</style>