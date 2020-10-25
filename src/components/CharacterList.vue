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
    border: 4px solid #369457;
    border-radius: 8px;
    padding: 16px;
    background-color: #1F6032;
    width: 26%;
    height: 400px;
    overflow-y:auto;
    

}

ul {
    list-style-type: none;
    padding-left: 0;  
    
}
</style>