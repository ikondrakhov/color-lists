<template>
  <div id="app-container">
    <div class="app-block">
      <DropDownList
        v-for="list in listsOfColors"
        :listId="list.id"
        :key="list.id"
        :colorsList="list"
      />
    </div>
    <div class="app-block">
      <ColorSquaresList
        v-for="list in listsOfColors"
        :key="list.id"
        :name="list.name"
        :colorsList="list"
      />
    </div>
  </div>
</template>

<script>
import DropDownList from "./components/DropDownList";
import ColorSquaresList from "./components/ColorSquaresList.vue";

export default {
  name: "App",
  data: function () {
    return {
      listsOfColors: this.$store.state.listsOfColors,
    };
  },
  components: {
    DropDownList,
    ColorSquaresList,
  },
};
</script>

<style>
#app {
  font-size: 12px;
}

#app-container {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  border: 1px solid black;
}

.app-block {
  border: 1px solid black;
  margin: 10px;
  padding: 10px;
  width: 40%;
}

@media screen and (max-width: 600px) {
  #app-container {
    flex-direction: column;
  }

  .app-block {
    box-sizing: border-box;
    width: 90%;
    align-self: center;
  }
}
</style>
