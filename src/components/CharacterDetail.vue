<template>
<section>

    <img :src="character.img" :alt="'Image of ' + character.name">
  <h1>{{character.name}}</h1>
  <p>Nickname: {{character.nickname}}</p>
  <p>Played by: {{character.portrayed}}</p>
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
img {
    height: 150px;
    width: 100px;
    object-fit: cover;
    margin-right: 10px;
}
</style>