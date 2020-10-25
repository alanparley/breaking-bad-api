<template lang='html'>
<section id='favourite-characters'>
    <h3>Favourite Characters</h3>
    <ul>
        <li v-for="favouriteCharacter in favouriteCharacters"><img :src="favouriteCharacter.img" id="smaller" alt="">{{ favouriteCharacter.name }}
        
        <br>
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
      border: 4px solid black;
    border-radius: 8px;
    padding: 16px;
    background: rgb(9,48,9);
background: linear-gradient(0deg, rgba(9,48,9,1) 23%, rgba(13,62,16,1) 39%, rgba(31,96,50,1) 61%, rgba(41,119,62,1) 83%, rgba(54,148,87,1) 95%);
    width: 26%;
    height: 400px;
    text-align: center;
}

#smaller {
    height: 50px;
    width: 30px;
    object-fit: cover;
    margin-right: 10px;
}
</style>