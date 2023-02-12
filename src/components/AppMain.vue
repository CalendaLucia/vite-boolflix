<script>
import FilmCard from './FIlmCard.vue';
import SerieCard from './SerieCard.vue';
import { store } from '../store';
export default {
    name:'AppMain',
    data() {
        return {
            store,
        }
    },
    components: {
      FilmCard,
      SerieCard,
    },
    methods: {
        scrollLeft () {
            this.current--;
        },
        scrollRight (){
            this.current++;
        }
    },
   

    }

</script>

<template>
    <main>
      <div class="continer-fluid myctn">
        <h2 class="text-white d-block p-3">Film</h2>
        <div class="container-fluid myflex">
            <div class="mycarousel" >
                <div class="cards">
                    <FilmCard v-for="film in store.films" :film="film" :key="film.id"/>
                </div>
            </div>
               <!-- PREV & NETX BUTTONS -->
            <div class="arrow film-left-arrow" @click="scrollLeft">
              <i class="bi bi-caret-left-fill"></i>
            </div>
            <div class="arrow film-right-arrow" @click="scrollRight">
              <i class="bi bi-caret-right-fill"></i>
            </div>   
        </div>
        <h2 class="text-white p-3">Serie TV</h2>
        <div class="container-fluid myflex">
            <div class="mycarousel" >
                <div class="cards">
                    <SerieCard v-for="serie in store.series" :serie="serie" :key="serie.id"/>
                </div>
            </div>
                <!-- PREV & NETX BUTTONS -->
            <div class="arrow film-left-arrow" @click="scrollLeft">
             <i class="bi bi-caret-left-fill"></i>
            </div>
            <div class="arrow film-right-arrow" @click="scrollRight">
              <i class="bi bi-caret-right-fill"></i>
            </div>  
        </div>
      </div>
    </main>
</template>

<style lang="scss" >
@use '../styles/partials/mixins.scss' as *;

main {
    background-color:  #202020;
    width: 100%;

    .myctn {
     position: relative;

     .myflex {
      
        .mycarousel {
           width: 100%;
           margin: 0px 30px;
           padding: 50px 0px;
           overflow: hidden;

           .cards {
            width: 100%;
            @include flex (flex-start, center);
            overflow: hidden;
           }
        }

        .arrow {
          position: absolute;
          transform: translateY(-50%);
          font-size: 50px;
          color: #fff;
          cursor: pointer;
          z-index: 1;

           &.left-arrow {
               left: 0px;
               top: 28%;
           
            }

           &.film-left-arrow {
               left: 0px;
               top: 78%;
         } 

            &.right-arrow {
                 right: 0px;
                 top: 28%;
             }
             &.film-right-arrow {
                right: 0px;
                top: 78%;
            }
             
        
     }
     }

}

}


</style>