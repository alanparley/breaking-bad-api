<template>
  <li v-on:click="handleClick">
       <img :src="character.img" :alt="'Image of ' + character.name">
       <span>{{ character.name }}</span>
     
  </li>
</template>

<script>
import { eventBus } from "@/main.js"

export default {
    name: 'character-list-item',
    props: ['character'],
    methods: {
        handleClick: function(event) {
            eventBus.$emit("character-selected", this.character)
        }
    }

};
</script>

<style scoped>
li {
    display: flex;
    align-items: center;
    margin: 5px 0 5px 0;
    cursor: pointer;

}
img {
    height: 50px;
    width: 30px;
    object-fit: cover;
    margin-right: 10px;
}

</style>