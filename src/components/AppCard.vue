<script>
import { store } from '../store';
export default {
    name:'AppCard',
    data() {
        return {
            store
        }
    },
    props: {
        film:Object,
        serie:Object
    }

}
</script>

<template>
  
        <div class="card">
           <img :src="generateImageURL(film.poster_path)">
           <h3>{{ film.title}}</h3>
           <h4 v-if="film.original_title != film.title">{{ film.original_title}}</h4>
           <img :src="flag(film.original_language)">
           <h5>{{ film.original_language}}</h5>
           <div v-for="i in calculateStars(film.vote_average)" :key="i">
              <i class="bi bi-star-fill"></i>
           </div>
           <div v-for="i in (5 - calculateStars(film.vote_average))" :key="i">
             <i class="bi bi-star"></i>
           </div>
      </div>
    
</template>

<style lang="scss"></style>