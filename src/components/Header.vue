<template>
  <header>
    <div class="logo">
        <img src="../assets/img/logo.png" alt="" />
    </div>
    <div class="input_box">
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
    padding: 1.875rem 3.125rem;
    background-color: $primaryBlack;
    max-height: 4.375rem;

    .logo{
        max-width: 6.25rem;

        img{
            width:100%
        }
    }

    .input_box{
        border: 1px solid $primaryWhite;

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