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
 background: rgb(9,48,9);
background: linear-gradient(180deg, rgba(9,48,9,1) 0%, rgba(13,62,16,1) 29%, rgba(31,96,50,1) 51%, rgba(41,119,62,1) 70%, rgba(54,148,87,1) 87%);
  color: white;
  margin: 0px;
  padding: 0px;
  font-size: 15px;

  
  
}

.main-container {
  display: flex;
  justify-content:space-between;
  margin-left: 100px;
  margin-right: 100px;
  padding: 10px;
  border: solid 4px white;
  border-radius: 8px;

  
  
}

header {
  margin: 0%;
  background: rgb(9,48,9);
background: linear-gradient(90deg, rgba(9,48,9,1) 0%, rgba(13,62,16,1) 28%, rgba(31,96,50,1) 61%, rgba(41,119,62,1) 81%, rgba(54,148,87,1) 93%);
  color: white;
  text-align: center;
  font-size: 10pt;
}

footer {
  margin: 0%;
  background: rgb(9,48,9);
background: linear-gradient(270deg, rgba(9,48,9,1) 0%, rgba(13,62,16,1) 28%, rgba(31,96,50,1) 61%, rgba(41,119,62,1) 81%, rgba(54,148,87,1) 93%);
  color: white;
  text-align: center;
  font-size: 10pt;
}
</style>