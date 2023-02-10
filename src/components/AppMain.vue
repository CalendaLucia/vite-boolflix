<script>
import AppCard from './AppCard.vue';
import { store } from '../store';
export default {
    name:'AppMain',
    data() {
        return {
            store
        }
    },
    components: {
       AppCard
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
        <AppCard v-for="(film, index) in store.films" :key="index" :item="film"/>
        <AppCard v-for="(serie, index) in store.series" :key="index" :item="serie"/>
    </div>
</template>

<style lang="scss"></style>