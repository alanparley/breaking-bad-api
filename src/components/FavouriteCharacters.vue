<template lang='html'>
<section id='favourite-characters'>
    <h3>Favourite Characters</h3>
    <ul>
        <li v-for="favouriteCharacter in favouriteCharacters"><img :src="favouriteCharacter.img" id="smaller" alt="">{{ favouriteCharacter.name }}
        <br>
        <button v-on:click="updateFavourites(favouriteCharacter)"> remove</button>
        </li>
        
     </ul>
</section>
  
</template>




<script>


import { eventBus } from "@/main.js";

export default {
    name: 'favourite-characters',
    props: ['favouriteCharacters', 'favouriteCharacter'],

    data(){
        return {
            selectedFavouriteCharacter: null
        }
    },


    methods: {
        updateFavourites: function(favouriteCharacter) {
            this.selectedFavouriteCharacter = favouriteCharacter;

            eventBus.$emit('favourite-selected', this.selectedFavouriteCharacter)
        }
    }
}
</script>


<style>

li {
    display: flex;
    align-items: center;
    margin: 5px 0 5px 0;
    cursor: pointer;

}   

#favourite-characters {
    border: 4px solid #369457;
    border-radius: 8px;
    padding: 16px;
    background-color: #1F6032;
    width: 26%;
    height: 400px;
}

#smaller {
    height: 50px;
    width: 30px;
    object-fit: cover;
    margin-right: 10px;
}
</style>