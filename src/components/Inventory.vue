<template>
  <div id="inventory">
    <h2>Inventory</h2>
    <span v-if="empty">Empty</span>
    <ul v-else>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Inventory",
  data() {
    return {
      empty: true,
      key: false,
      teddy: false
    };
  }
};
</script>
<style lang="scss" scoped>
@import "../scss/main.scss";
#inventory {
  @extend %reset;
  text-align: center;
  width: 25vmax;
  height: 25vmax;
  li {
    list-style: none;
  }
}
</style>


