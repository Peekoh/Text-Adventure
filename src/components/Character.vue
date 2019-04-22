<template>
  <div id="character-sheet">
   

    <ul> 
      <h2>Status</h2>
      <li>HP:{{hp}}%</li>
      <li>Sanity:{{sanity}}%</li>
      <li>Gold:{{gold}}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Character",
  data() {
    return {
      hp:100,
      gold:10,
      sanity:100,
    }
  },
  mounted: function() {
   
  
    /* fetch("/api/data/character.json")
      .then(results => results.json())
      .then(results => {
        this.character = results;
        this.nm = this.character.nm;
        this.hp = this.character.hp;
        this.sanity = this.character.mp;
        this.gold = this.character.gold;
      }); */
  }
}
</script>
<style lang="scss" scoped>
@import "../scss/main.scss";
#character-sheet {
    @extend %reset;
  text-align: center;
  width: 25vmax;
  height:25vmax;
  li {
    list-style: none;
  }
}
</style>

