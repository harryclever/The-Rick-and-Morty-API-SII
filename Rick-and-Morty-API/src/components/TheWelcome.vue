<script setup>
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
<div class="centro">
  <img class="first-logo" src="../assets/img/Rick_and_Morty.svg.png" alt="Rick_and_Morty-logo">
 <div class="buscador">
  <h1>Buscar Personajes</h1>
  <input type="text" v-model="search" placeholder="Buscar">
  
 </div>
 <div class="selector">
    <div id="Next">
      <button  class="Next" c v-on:click="increment">Siguente</button>
    </div>
    <h1>Pagina: {{counter}}</h1>
    
    <div id="previus">
      <button class="previus" @keypress="decrement"  v-on:click="decrement">Aunterior</button>
    </div>
  </div>
<div class="content">
  <div id="card" class="box-img"   v-for="character in filterSearch " :key="character">
  <div class="img-box">
    <img class="zoom" :src="character.image" alt="">
  </div>
  <main class="box">
    <h2>{{character.name}}</h2>
  <h3>{{character.gender}}</h3>
  <h3>{{character.location.name}}</h3>
  <h3>{{character.status}}</h3>
  <h3>{{character.species}}</h3>
  </main>
  
</div>
</div>

</div>
<div class="footer">
 
</div>
</template>

<script>
import axios from 'axios'
import { computed } from '@vue/runtime-core'

export default {
  components: {

  },
  data() {
    return {
      search: '',
      characteres: [],
      counter: 1,
      
     
      
      
      
    }
  },
  mounted() {
    this.getTodos();
    this.increment();
    this.decrement();
    
    
  },
  methods: {

    getTodos() {
      let page =this.counter;
      this.axios.get('https://rickandmortyapi.com/api/character?page=' + page)
      .then(res => 
      (this.characteres = res.data.results)
      )
      .catch(e => {
        console.log(e)
      })
      
    },
    increment() {
      if(this.counter <= 41) {
        this.counter++;
      this.getTodos()
      }
    },
    decrement() {
      if(this.counter >= 2) {
        this.counter--;
      this.getTodos()
      }
      
    }
    

  },
  computed: {
    filterSearch() {
      return this.characteres.filter(post => {
        return post.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
    
  
  }
  
}

</script>

<style>

.zoom {
    transition: transform .2s; 
}
 
.zoom:hover {
    transform: scale(1.1); 
}
.zoom:hover {
    transform: scale(1.1); 
}

.selector {
    display: flex;
    gap: 4rem;
    flex-direction: row-reverse;
    align-items: center;
}

button.Next {
    background-color: hsla(160, 100%, 37%, 1);
    font-weight: 700;
    padding: 6px 0;
    padding-left: 2rem;
    padding-right: 2rem;
    font-size: 16px;
    color: black;
    border-radius: 10px;
    margin-top: 5px;
    cursor: pointer;
}
button.previus {
    background-color: hsla(160, 100%, 37%, 1);
    font-weight: 700;
    padding: 6px 0;
    padding-left: 2rem;
    padding-right: 2rem;
    font-size: 16px;
    color: black;
    border-radius: 10px;
    margin-top: 5px;
    cursor: pointer;
}
h3 {
  padding-bottom: 4px;
    padding-top: 4px;
   font-size: 700;
   color: black;
    background-color:#F4F6F7;
    border-radius: 10px;
    margin-top: 6px;
    padding-right: 6px;
    padding-left: 6px;
    font-weight: 600;
}
.buscador {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 1rem;
    background: rgb(60, 62, 68);
    margin-bottom: 1rem;
    padding: 2px;
    padding-right: 12px;
    padding-left: 12px;
    border-radius:10px;
    
}
input {
  background:white;
  outline: none;
  border: 0;
  padding: 8px;
  color:black;
  font-weight: 700;
  border-radius:10px;
  text-align: center;
}
img.first-logo {
    width: 45%;
    height: auto;
    margin-bottom: 0.6rem;
    margin: 1rem;
}

img {
    height: 15rem;
    width: 17rem;
    padding-top: 7px;
    padding-right: 7px;
    padding-left: 7px;
    border-radius: 1rem;
}
h1 {
  color: hsla(160, 100%, 37%, 1);
  font-weight: 700;
}
h2 {
  background-color: hsla(160, 100%, 37%, 1);
    font-weight: 700;
    padding: 6px 0;
    padding-left: 2rem;
    padding-right: 2rem;
    font-size: 16px;
    color: black;
    border-radius: 10px;
    margin-top: 5px;
}
.box-img {
  background: rgb(60, 62, 68);
  margin-bottom: 1rem;
  border-radius: 10px;
  padding-bottom: 14px;
}
.centro {
    display: flex;
    align-items: center;
    flex-direction: column;
}
main.box {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 0.5rem;
}
.content {
  display: flex;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr;
    gap: 17px 20px;
    align-items: center;
    flex-wrap: wrap;
    justify-content: center;
    margin: 3rem;
}
@media(max-width: 760px) {
  .buscador {
    display: flex;
    gap: 1rem;
    background: rgb(60, 62, 68);
    margin-bottom: 1rem;
    padding: 2px;
    padding-right: 12px;
    padding-left: 12px;
    border-radius: 10px;
    flex-direction: column;
    align-items: stretch;
    
}
} 
</style>