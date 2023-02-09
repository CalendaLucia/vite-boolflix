<script>
import { store } from '../store';
export default {
    name:'AppMain',
    data() {
        return {
            store
        }
    },
}
</script>

<template>
    <div class="continer-fluid">
      <div class="card">
        <div  v-for="film in store.films" :key="film.id">
           <h3>{{ film.title}}</h3>
           <h4>{{ film.original_title}}</h4>
           <h5>{{ film.original_language}}</h5>
           <h6>{{ film.vote_average}}</h6>
        </div>
      </div>
    </div>
</template>

<style lang="scss"></style>