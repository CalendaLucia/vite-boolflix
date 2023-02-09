<script>
import axios from 'axios'
import { store } from './store';
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import AppCard from './components/AppCard.vue'


export default {
  name:'App',
  data() {
    return {
      store,
    

    }
  },
  components: {
    AppHeader,
    AppMain,
    AppCard,
  },

  methods: {
    event () {
      this.search('movie');
      this.search('tv');
    },
    search(endpoint) {
        let url ='https://api.themoviedb.org/3/search/'; 
        console.log(this.store.searchText);

        axios
          .get( url + endpoint, {
            params: {
              api_key:'2746a71b87fe359c777070f31413f587',
              query: this.store.searchText,
              language: 'it-IT'
            }
          })
          .then(response => {
            console.log(response);

            if (endpoint == 'movie') {
              this.store.films = response.data.results;
            }
            else {
              this.store.series = response.data.results;
            }
          
            
          })
           .catch(error => {
            console.error(error);
        });
        
      }
      
    }
   


};


</script>

<template>
  <AppHeader @search="event"/>

  <AppMain/>
  <AppCard/>

</template>

<style lang="scss">
@import './styles/partials/main.scss'
</style>
