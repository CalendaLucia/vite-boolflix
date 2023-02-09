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
    <div>
        <ul>
             <li class="bg-light" v-for="film in store.films">
                   {{ film.title }}
              </li>
          </ul>
    </div>
</template>

<style lang="scss"></style>