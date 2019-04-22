<template >
  <!--v-cloak hides attributes while mounting move to output
  ADD IF ELSE LOGIC-->
  <div id="app" v-cloak>
    <div class="scanlines">
      <Header/>

      <Output/>

     <div id="info">
        <Character/>
        <Inventory/>
     </div>
     
    </div>
  </div>
</template>

<script>
import Header from "./components/layout/Header.vue";
import Character from "./components/Character.vue";
import Output from "./components/Output.vue";
import Inventory from "./components/Inventory.vue";

export default {
  name: "app",
  components: {
    Header,
    Character,
    Output,
    Inventory
    // Output
    //axios
  },
  data() {
    return {
      /* room: null,
      roomDesc: "",
      input: "",
      rooms: null,
      initialRoom: "Entrance", */
      //  loading:true,
    };
  }
};
</script>
<style lang="scss">
@import "./scss/main.scss";
@import "./scss/scanlines.scss";

</style>


