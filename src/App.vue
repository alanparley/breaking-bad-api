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

    eventBus.$on('favourite-selected', (character) => {
      this.favouriteCharacters.unshift(character)
    })
  },
  

};
</script>

<style>

main {
  font-family: Arial, Helvetica, sans-serif;
  color: darkgreen;
  font-size: 15px;
}

.main-container {
  display: flex;
  justify-content: space-between;
}

header {
  margin: 0%;
  background-color: black;
  color: white;
  text-align: center;
  font-size: 10pt;
}
</style>