<script>

import { store } from '../store';
export default {
    name:'AppMain',
    data() {
        return {
            store
        }
    },
    methods: {
        flag(lang) {
            switch (lang) {
                case 'en':
                    lang = 'uk';
                    break;

                case 'pt':
                    lang = 'po';
                    break;

                case 'es':
                    lang = 'sp';
                    break;
            }
            const flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;
            return flag;
        },
        generateImageURL(posterPath, size = 'w342') {
           return `https://image.tmdb.org/t/p/${size}/${posterPath}`;
        },
        calculateStars(vote) {
          return Math.ceil(vote / 2);
        },
}
    }

</script>

<template>
    <div class="continer-fluid">
      <div class="card">
        
        <div v-for="film in store.films" :key="film.id">
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
      </div>
    </div>
</template>

<style lang="scss"></style>