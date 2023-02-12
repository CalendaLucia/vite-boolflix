<script>
import { store } from '../store';
export default {
    name:'SerieCard',
    data() {
        return {
            active: null,
            store
        }
    },
    props: {
    serie: {
        type: Object,
        required: true
    }
  },
  
    methods: {
      flagClass(lang) {
      return `flag-icon-${lang}`;
      },
        generateImageURL(posterPath, size = 'w342') {
           return `https://image.tmdb.org/t/p/${size}/${posterPath}`;
        },
        calculateStars(vote) {
          return Math.ceil(vote / 2);
        },
        setActive(serie) {
  setTimeout(() => {
    this.active = serie;
  }, 1000)
}
     }

}
</script>

<template>
    <div class="mycard" @mouseenter="setActive(serie)" @mouseleave="setActive(null)">
      <img :src="generateImageURL(serie.poster_path)" class="card-img-top">
      <div class="card-body" v-if="active === serie">
         <ul class="list-group list-group-horizontal" v-if="active === serie">
           <li class="list-group-item">
             <i class="bi bi-play-circle-fill"></i>
           </li>
           <li class="list-group-item">
             <i class="bi bi-plus-circle"></i>
           </li>
           <li class="list-group-item">
             <i class="bi bi-hand-thumbs-up"></i>
           </li>
           <li class="list-group-item">
             <i class="bi bi-arrow-down-circle"></i>
           </li>
         </ul>
         <h5 class="card-title">{{ serie.name }}</h5>
         <h4 v-if="serie.original_title != serie.name">{{ serie.original_title}}</h4>
         <div class="d-inline-block" v-for="i in calculateStars(serie.vote_average)" :key="i">
           <i class="bi bi-star-fill"></i>
         </div>
         <div class="d-inline-block" v-for="i in (5 - calculateStars(serie.vote_average || serie.vote_average))" :key="i">
           <i class="bi bi-star"></i>
         </div>
         <p class="card-text mt-2">{{ serie.overview }}</p>
        </div>      
        <div class="card-body" v-if="active === serie">
          <span class="flag-icon" :class="flagClass(serie.original_language)"></span>
       </div> 
    </div>  
</template>

<style lang="scss" scoped>
@use '../styles/partials/cards.scss' as *;
</style>