<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import AppCard from './components/AppCard.vue'
import axios from 'axios'
import { store } from './store';

export default {
  name:'App',
  data() {
    return {
      store

    }
  },
  components: {
    AppHeader,
    AppMain,
    AppCard,
  },

  methods: {
    search() {
        let url ='https://api.themoviedb.org/3/search/movie'; 
        console.log(this.store.searchText);

        axios
          .get( url, {
            params: {
              api_key:'2746a71b87fe359c777070f31413f587',
              query: this.store.searchText,
              language: 'it-IT'
            }
          })
          .then(response => {
            console.log(response);
            this.store.films = response.data.results;
            
          })
           .catch(error => {
            console.error(error);
        });
        
      }
      
    }
   


};


</script>

<template>
  <AppHeader @search="search"/>
  <AppMain/>
  <AppCard/>

</template>

<style lang="scss">
@import './styles/partials/main.scss'
</style>
