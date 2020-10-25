<template>
  <main>
    <header>
      <h1>Breaking Bad API</h1>
    </header>
    <section class="main-container">
    <character-list :characters="characters"></character-list>
    <character-detail :character='selectedCharacter' :favouriteCharacters='favouriteCharacters'></character-detail>
    <favourite-characters :favouriteCharacters='favouriteCharacters'></favourite-characters>
    </section>
    <footer> 
      <h1>Breaking Bad API</h1>
    </footer>
  </main>
</template>

<script>

import CharacterList from '@/components/CharacterList';
import CharacterDetail from '@/components/CharacterDetail'
import FavouriteCharacters from './components/FavouriteCharacters.vue'
import { eventBus } from '@/main.js'

export default {
  name: 'app',
  data() {
    return {
      characters: [],
      selectedCharacter: null,
      favouriteCharacter: null,
      CharacterDetail: null,
      favouriteCharacters: []
    };
  },

    components: {
      CharacterList,
      CharacterDetail,
      'favourite-characters':FavouriteCharacters
    },
    
  mounted (){
    fetch('https://breakingbadapi.com/api/characters')
    .then (res => res.json())
    .then (characters => this.characters = characters)

    eventBus.$on("character-selected", (character) => {
      this.selectedCharacter = character;
    });

    eventBus.$on("favourite-picked", (character) => {
      this.favouriteCharacter = character;
    });

    eventBus.$on('favourite-selected', (character) => {
      this.favouriteCharacters.unshift(character)
    })
  },
  

};
</script>

<style>



main {
  font-family: Arial, Helvetica, sans-serif;
 background-image: url("https://www.desktopbackground.org/p/2010/07/21/51793_breaking-bad-smoke-backgrounds_2448x2448_h.jpg");
  color: white;
  font-size: 15px;

  
  
}

.main-container {
  display: flex;
  justify-content:space-between;
  margin-left: 100px;
  margin-right: 100px;
  padding: 10px;
  border: solid 4px black

  
  
}

header {
  margin: 0%;
  background-color: black;
  color: white;
  text-align: center;
  font-size: 10pt;
}

footer {
  margin: 0%;
  background-color: black;
  color: white;
  text-align: center;
  font-size: 10pt;
}
</style>