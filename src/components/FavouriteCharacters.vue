<template lang='html'>
<section id='favourite-characters'>
    <h3>Favourite Characters</h3>
    <ul>
        <li v-for="favouriteCharacter in favouriteCharacters" :key='favouriteCharacter'>Name: {{ favouriteCharacter.name }}</li>
     </ul>
</section>
  
</template>




<script>

import { eventBus } from "@/main.js";

export default {
    name: 'favourite-characters',
    props: ['favouriteCharacters']
}
</script>


<style>

</style>