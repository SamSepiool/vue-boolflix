<template>
    

    <div class="card">
        <div class="poster">
            <img v-if='api.poster_path'  :src="`https://image.tmdb.org/t/p/w342/${api.poster_path}`" alt="">

            <img v-else src="../assets/img/placeholder.png" alt="">
        </div>

        
        <ul class="info">
            <li> <strong>Title:</strong> {{api.title || api.name}}</li>

            <li v-if="api.original_title !== api.title || api.original_name !== api.name"><strong>Original title:</strong> {{api.original_title || api.original_name}}</li>

            <li><strong>Original language:</strong> <lang-flag :iso="api.original_language" :squared="false"/></li>

            <li> <strong>Vote:</strong>
                <font-awesome-icon class="star_solid" v-for="(solid, index) in starsVote(api)" :key="index"   :icon='starSolid'/>
                <font-awesome-icon v-for="(empty, index) in (5 - starsVote(api))" :key="`other`+index"   :icon='starEmpty'/>
            </li>

            <li v-if="api.overview" ><strong>Overview:</strong><p>{{api.overview}}</p></li>

        </ul>
    </div>

   
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import { faStar as fasStar } from '@fortawesome/free-solid-svg-icons';
import { faStar as farStar } from '@fortawesome/free-regular-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
    name: 'Card',
    props:{
        api: Object, 
    },
    components:{
        LangFlag,
        FontAwesomeIcon
        
    },
    data(){
        return{
            starSolid: fasStar,
            starEmpty: farStar,
        }
    },
    methods:{

        starsVote(obj){
        return Math.ceil(obj.vote_average / 2)
       }

    }

}
</script>


<style lang='scss' scoped>
@import '../assets/style/variables.scss';

.card{
    position: relative;
    margin: .625rem;
    background-color: $primaryGray;
    font-size: 1rem;

    &:hover{
        cursor:pointer;
        box-shadow: inset 0px 2px 5px 1px $primaryBlue;
        overflow-y: scroll;

    }
    
    .poster{
        width: 100%;
        height: 25rem;
        transition: .8s ease-out;
        img{
            width: 100%;
            height: 25rem;
            object-fit: cover;
        }
    }

    &:hover .poster{
        opacity:0;
        transform: rotatey(180deg);
    }


    .info{
        position: absolute;
        top: 0;
        // display: flex; COMMON
        flex-direction: column;
        width: 100%;   
        padding: .625rem;
        opacity: 0;


        li{
            margin: .3125rem 0;
        }
        p{
            margin: 1rem 0;
        }
        .star_solid{
            color: $starGold;
        }
    }

        &:hover .info{
        opacity:1;
        transition: 1s;
    }
}

// .card{
//     width: 100%;
//     background-color: $primaryGray;
//     // margin: .3125rem;
//     display: flex;
//     overflow: hidden;
//     position: relative;
    
//     .poster{
//         transition: .8s ease-out;
//         width: 100%;

//         img{
//             width: 100%;
//             height: 21.875rem; 
//             object-fit: cover;
//         }
//     }

//     &:hover{
//         cursor:pointer;
//         box-shadow: inset 0px 2px 5px 1px $primaryBlue;
//     }
    
//     &:hover .poster{
//         opacity:0;
//         transform: rotatey(180deg);
//     }

//     .info{
//     opacity:0;
//     padding: .625rem;
//     display: flex;
//     flex-direction: column;
//     position: absolute; 

//         li{
//             margin: .3125rem 0;
//         }
//         p{
//             margin: 1rem 0;
//             overflow-y:scroll;
//         }
//         .star_solid{
//             color: $starGold;
//         }
//     }

//     &:hover .info{
//         opacity:1;
//         transition: 1s;
//     }

// }




</style>