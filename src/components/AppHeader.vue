<script>
import { store } from '../store';
export default {
  name:'AppHeader',
  data() {
    return {
      store
      
    }
  },

};

</script>

<template>
  <div class="container-fluid">
    <nav class="navbar bg-light">
      <div class="container-fluid">
          <input v-model="store.searchText" class="form-control me-2" type="search" placeholder="Search" aria-label="Search" >
          <button class="btn btn-outline-success" type="submit" @click="$emit('search')">Search</button>
      </div> 
    </nav>
  </div>
</template>

<style lang="scss" scoped>

</style>
