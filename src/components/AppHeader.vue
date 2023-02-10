<script>
import { store } from '../store';
export default {
  name:'AppHeader',
  data() {
    return {  
      store,
      show: false,
      menuItems: [
      { label: 'Home', href: '#' },
      { label: 'Serie Tv', href: '#' },
      { label: 'Film', href: '#' },
      { label: 'Originals', href: '#' },
      { label: 'Aggiunti di recente', href: '#' },
      { label: 'La mia lista', href: '#' }
    ],   
    }
  },
}

</script>

<template>
  <header>
    <div class="container-fluid">
      <nav class="navbar">
         <div class="container-fluid">
           <div class="menu left">
              <h1 class="text-danger h3">BOOLFLIX</h1>
              <div class="menu-list">
                <ul class="list-group list-group-horizontal">
                  <li class="item" v-for="item in menuItems" :key="item.id">
                    <a :href="item.href">
                       {{ item.label }}
                    </a>
                  </li>
                </ul>
              </div>
           </div>
           <div class="menu right list-group list-group-horizontal">
             <ul class="list-group list-group-horizontal">
               <li class="item">
                 <a href="#">
                   <i class="bi bi-search" @click="show = !show"></i>
                   <div class="ctn-search-bar" v-show="show">
                     <input v-model="store.searchText" class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
                     <button class="btn btn-outline-danger"  @click="search">Search</button>
                   </div>
                 </a>
               </li>
               <li>
                <a href="#">BAMBINI</a>
               </li>
               <li class="bell">
                <a href="#">
                  <i class="bi bi-bell-fill"></i>
                  <span class="notification-badge">1</span>
                </a>
               </li>
               <li>
                  <a title="Shadowak47, CC BY-SA 4.0 &lt;https://creativecommons.org/licenses/by-sa/4.0&gt;, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Netflix-avatar.png">
                    <img class="profile" width="30" alt="Netflix-avatar" src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Netflix-avatar.png">
                    <i class="bi bi-caret-down-fill"></i>
                  </a>
               </li>
             </ul>
           </div>
         
         </div>
      </nav>
    </div>
  </header>
  
</template>

<style lang="scss" scoped>
@use '../styles/partials/main.scss' as *;
header {
  background-color: #202020;

  .menu {
   @include flex (space-around, baseline);
    
  h1 {
    padding-right: 20px;
  }
  .list-group   {
     
     li {
       padding: 0px 8px;
       list-style: none;

       .bi-search {
        font-size: 18px
       }

         a {
           color: #b4b4b4;
           text-decoration: none;
           font-size: 12px;

           &:hover {
             color: white;
           }
         } 
     }
  }

  .bell {
  position: relative;

  .bi-bell-fill {
    font-size: 18px;
  }

  .notification-badge {
    display: inline-block;
    background-color: red;
    position: absolute;
    top: 5px;
    right: 7px;
    color: white;
    border-radius: 50%;
    width: 10px;
    height: 10px;
    text-align: center;
    font-size: 6px; 
  }
}


 
.profile {
  padding-right: 3px;
}
}


}




</style>
