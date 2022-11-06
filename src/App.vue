<script>
export default {
  // reactive state
  data() {
    return {
      count: 1,
      triangle: ""
    }
  },

  // functions that mutate state and trigger updates
  methods: {
    increment() {
      this.count++;
      this.renderTriangel()
    },
    decrement() {
      this.count--
      this.renderTriangel()
    },
    renderTriangel() {
      let result = "";
      const symbol = "▲";
      const emptySymbol = "_";

      for (let I = 0; I <= this.count; I++) {
        result += "<p>";
        for (let J = this.count; J > I; J--) {
          result += emptySymbol;
        }
        for (let J = 0; J <= I; J++) {
          result += symbol;
        }
        result += "</p>";
      }

      this.triangle = result;
    }
  },

  // lifecycle hooks
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <div v-html=triangle></div>
  <button @click="increment">Uvelichetit</button>
  <button @click="decrement">Umenshit</button>
</template>
