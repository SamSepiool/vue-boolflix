<template>

    <div class="wrapper">
        <h2>Series</h2>

        <ul>
            <li v-for="(series, index) in tvSeries" :key="index"> 
                TITLE: {{series.name}}
                ORIGINAL TITLE: {{series.name}}
                LANG: {{series.original_language}}
                <lang-flag :iso="series.original_language" :squared="false"/>
                VOTO: {{series.vote_average}}
            </li>
        </ul>
    </div>
  
</template>

<script>
import LangFlag from 'vue-lang-code-flags';


export default {
    name: 'Series',
    props:{
        tvSeries: Array,
    },
    components:{
        LangFlag,
    }

}
</script>

<style>

</style>