<template>
  <header>
   
    <div class="logo">
        <a href="#"><img src="../assets/img/logo.png" alt="" /></a>
    </div>

    <div class="anchor">
      <a href="#films">MOVIES</a>
      <a href="#series">SERIES</a>
    </div>



  <div class="input_box ">
      <button @click="$emit('passInput', searchInput)">
          <font-awesome-icon   :icon='search'/>
      </button>
      <input placeholder="Titoli, persone, generi" type="text" v-model="searchInput" />
  </div>
         
     
    
  </header>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faSearch as fasSearch } from '@fortawesome/free-solid-svg-icons';

export default {
  name: "Header",
  components:{
      FontAwesomeIcon
  },

  data() {
    return {
      searchInput: "",
      search: fasSearch,
    };
  },
};
</script>

<style lang='scss' scoped>
@import '../assets/style/variables.scss';


header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: .75rem;
  background-color: $primaryBlack;
  max-height: 4.375rem;
  position: fixed;
  z-index: 10;
  width: 100%;
  box-shadow:  0px 0px 20px -4px $primaryWhite;



  .logo{
    width: 10%;
    min-width: 3.125rem;

    img{
      width:100%;
      
    }
  }

  .anchor{
    a{
      margin: .75rem;
    }
  }

  .input_box{
    border: 1px solid $primaryWhite;
    display: flex;
    min-width: 3.125rem;
    overflow: hidden;

    input,
    button{
      padding: .3125rem .625rem;
      background-color: transparent;
      border: none;
      color: $primaryWhite;

    }
  }

   
}
</style>