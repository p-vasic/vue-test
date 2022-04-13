<template>
  <div>
    <div>Name: {{ info.name }}</div>
    <div>Age: {{ info.age }}</div>
    <div>Where do you live: {{ country }}</div>
    <div>Package: {{ tpackage }}</div>
    <div>Premium: {{ premium }}</div>
    <div>
      <button @click="$emit('update-step', 1)">Prev</button>
      <button @click="$emit('update-step', 0)">Buy</button>
    </div>
  </div>
</template>

<script>
export default {
  inject: ["info"],
  computed: {
    country() {
      const countries = {
        hkd: "Hong Kong",
        usd: "United States",
        aud: "Australia",
      };
      return countries[this.info.country];
    },
    tpackage() {
      if (this.info.premium === "500") {
        return "Standard";
      } else if (this.info.premium === "250") {
        return `Safe(+250${this.info.country.toUpperCase()}, 50%)`;
      } else {
        return `Safe(+375${this.info.country.toUpperCase()}, 75%)`;
      }
    },
    premium() {
      const multiply =
        this.info.country === "hkd" ? 1 : this.info.country === "usd" ? 2 : 3;
      return `${
        this.info.age * 10 * multiply
      }${this.info.country.toUpperCase()}`;
    },
  },
};
</script>