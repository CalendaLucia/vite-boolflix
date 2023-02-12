<script>
import { store } from '../store';
export default {
    name:'FilmCard',
    data() {
        return {
            active: null,
            store
          
        }
    },

    props: {
    film: {
      type: Object,
      required: true
    },
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
        setActive(film) {
           setTimeout(() => {
             this.active = film;
         }, 1000)
       }
     }

}
</script>

<template>
       <div class="mycard" @mouseenter="setActive(film)" @mouseleave="setActive(null)">
         <img :src="generateImageURL(film.poster_path)" class="card-img-top">
         <div class="card-body" v-if="active === film">
            <ul class="list-group list-group-horizontal" v-if="active === film">
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
            <h5 class="card-title">{{ film.title }}</h5>
            <h4 v-if="film.original_title != film.title">{{ film.original_title}}</h4>
            <div class="d-inline-block" v-for="i in calculateStars(film.vote_average)" :key="i">
              <i class="bi bi-star-fill"></i>
            </div>
            <div class="d-inline-block" v-for="i in (5 - calculateStars(film.vote_average))" :key="i">
              <i class="bi bi-star"></i>
            </div>
            <p class="card-text mt-2">{{ film.overview }}</p>
           </div>      
           <div class="card-body" v-if="active === film">
            <span class="flag-icon" :class="flagClass(film.original_language)"></span>
          </div> 
       </div>
</template>
  

<style lang="scss" scoped>
@use '../styles/partials/cards.scss' as *;
</style>