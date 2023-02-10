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

    }

</script>

<template>
    <div class="continer-fluid myctn">
       <AppCard v-for="film in store.films" :film='film' :key="film.id"/>
        <!-- <AppCard v-for="(serie, index) in store.series" :key="index" :item="serie"/>  -->
     
    </div>
</template>

<style lang="scss">
@use '../styles/partials/mixins.scss' as *;

.myctn {
   @include flex (space-around, center);
   width: 100%;
   padding: 20px 20px;
   background-color: rebeccapurple;
   margin: 0 auto;
   overflow-x: scroll;
  white-space: nowrap;

}
</style>