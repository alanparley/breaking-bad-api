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
    border: 4px solid #369457;
    border-radius: 8px;
    padding: 16px;
    background-color: #1F6032;
    width: 30%;
    height: 400px;

}


img {
    height: 150px;
    width: 100px;
    object-fit: cover;
    margin-right: 10px;
}
</style>