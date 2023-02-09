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
        }
    }
}
</script>

<template>
    <div class="continer-fluid">
      <div class="card">
        <div  v-for="film in store.films" :key="film.id">
           <h3>{{ film.title}}</h3>
           <h4>{{ film.original_title}}</h4>
           <img :src="flag(film.original_language)">
           <h5>{{ film.original_language}}</h5>
           <h6>{{ film.vote_average}}</h6>
        </div>
      </div>
    </div>
</template>

<style lang="scss"></style>