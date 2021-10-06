<template>

    <div class="wrapper">
        <h2>Series</h2>

        <ul>
            <li v-for="(series, index) in tvSeries" :key="index"> 
                TITLE: {{series.name}}
                ORIGINAL TITLE: {{series.name}}
                LANG: {{series.original_language}}
                VOTO: {{series.vote_average}}
            </li>
        </ul>
    </div>
  
</template>

<script>

export default {
    name: 'Series',
    props:{
        tvSeries: Array,
    },

}
</script>

<style>

</style>