<template>
  <header>
      <input type="text" v-model='searchInput'>
      <button @click="$emit('passInput', searchInput)">Cerca</button>
  </header>
</template>

<script>
export default {

    name: 'Header',

    data(){
        return{

            searchInput: ''
        }
    }

}
</script>

<style>

</style>