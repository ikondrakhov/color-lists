<template>
  <div class="row">
    <input type="checkbox" v-model="isChecked" />
    <span class="color-name">{{ color.name }}</span>
    <input v-model="colorAmmount" type="number" min="0" />
    <input type="color" v-model="colorValue" />
  </div>
</template>

<script>
export default {
  name: "ColorInput",
  props: ["listId", "color"],
  computed: {
    colorAmmount: {
      get() {
        return this.$props.color.ammount;
      },
      set(value) {
        const listId = this.$props.listId;
        const newColor = Object.assign({}, this.$props.color);

        newColor.ammount = value;

        this.setColor({ listId, color: newColor });
      },
    },
    colorValue: {
      get() {
        return this.$props.color.value;
      },
      set(value) {
        const listId = this.$props.listId;
        const newColor = Object.assign({}, this.$props.color);

        newColor.value = value;

        this.setColor({ listId, color: newColor });
      },
    },
    isChecked: {
      get() {
        return this.$props.color.checked;
      },
      set(value) {
        const listId = this.$props.listId;
        const newColor = Object.assign({}, this.$props.color);

        newColor.checked = value;

        this.setColor({ listId, color: newColor });
      },
    },
  },
  methods: {
    setColor({ listId, color }) {
      this.$store.commit("setColor", {
        listId,
        newColor: color,
      });
    },
  },
};
</script>

<style scoped>
.color-name {
  height: 30px;
  line-height: 30px;
  text-align: center;
}

.row {
  display: flex;
  justify-content: baseline;
}

input[type="number"] {
  margin: 0;
  padding: 0;
  border: none;
  text-align: right;
  margin-right: 0;
  width: 50%;
}

input[type="number"]:focus-visible {
  border: none;
  outline: none;
}

input[type="color"] {
  border: none;
  background-color: transparent;
  resize: none;
  outline: none;
  width: 30px;
  height: 30px;
  vertical-align: middle;
  box-sizing: border-box;
  padding: 2px 4px;
}

input[type="checkbox"] {
  margin: 7px;
  width: 14px;
  height: 14px;
}
</style>
