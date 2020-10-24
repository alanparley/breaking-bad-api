<template>
<article>
    <img :src="character.img" :alt="'Image of ' + character.name">
  <h1>{{character.name}}</h1>
  <p>Nickname: {{character.nickname}}</p>
  <p>Played by: {{character.portrayed}}</p>
      </article>
</template>

<script>
export default {
    name: 'character-detail',
    props: ['character'],

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