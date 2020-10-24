<template>
  <ul>
      <character-list-item v-for="(character, index) in characters" 
      :key="index"
      :character="character">
      </character-list-item>

  </ul>
</template>

<script>

import CharacterListItem from "@/components/CharacterListItem";

export default {
    name: "character-list",
    components: {
        CharacterListItem
    },
    props : ["characters"],

}
</script>

<style>
ul {
    list-style-type: none;
    padding-left: 0;
}
</style>