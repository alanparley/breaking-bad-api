<template>
<section id="character-detail">
<h1>Character Details</h1>
    <img :src="character.img" :alt="'Image of ' + character.name">
  <h1>{{character.name}}</h1>
  <p>Nickname: {{character.nickname}}</p>
  <p>Played by: {{character.portrayed}}</p>
  <p>Occuptation: {{character.occupation.join(', &nbsp;').toString()}}</p>
  <button v-if="!favouriteCharacters.includes(character)"
  v-on:click='handleClick' :value="character">Add favourite character</button>
    

</section>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'character-detail',
    props: ['character', 'favouriteCharacters'],

    methods: {
        handleClick () {
            eventBus.$emit('favourite-selected', this.character)
        }
    },
}
</script>

<style>


#character-detail {
    border: 4px solid black;
    border-radius: 8px;
    padding: 16px;
    background: rgb(9,48,9);
background: linear-gradient(0deg, rgba(9,48,9,1) 23%, rgba(13,62,16,1) 39%, rgba(31,96,50,1) 61%, rgba(41,119,62,1) 83%, rgba(54,148,87,1) 95%);
    width: 26%;
    height: 400px;
    text-align: center;

}


img {
    height: 150px;
    width: 100px;
    object-fit: cover;
    margin-right: 10px;
    border: 2px solid black;
    border-radius: 3px;
}
</style>