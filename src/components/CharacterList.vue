<template>
  <section id='character-list'>
      <h1>Click a character for more info</h1>
  <ul class="scrolly">
      <character-list-item v-for="(character, index) in characters" 
      :key="index"
      :character="character">
      </character-list-item>

  </ul>
  </section>
</template>

<script>

import CharacterListItem from "@/components/CharacterListItem";

export default {
    name: "character-list",
    components: {
        'character-list-item': CharacterListItem
    },
    props : ["characters"],

}
</script>

<style>


#character-list {
        border: 4px solid black;
    border-radius: 8px;
    padding: 16px;
    background: rgb(9,48,9);
background: linear-gradient(0deg, rgba(9,48,9,1) 23%, rgba(13,62,16,1) 39%, rgba(31,96,50,1) 61%, rgba(41,119,62,1) 83%, rgba(54,148,87,1) 95%);
    width: 26%;
    height: 400px;
    overflow-y:auto;
    

}

ul {
    list-style-type: none;
    padding-left: 0;  
    
}
</style>