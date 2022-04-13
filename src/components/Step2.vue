<template>
  <div>
    <h1>Tell us about yourself</h1>
    <div>
      <label>Name: </label>
      <input type="text" v-model="name" />
    </div>
    <div>
      <label>Age: </label>
      <input type="text" v-model="age" />
    </div>
    <div>
      <label>Where do you live?</label>
      <select v-model="country">
        <option value="hkd">Hong Kong</option>
        <option value="usd">United States</option>
        <option value="aud">Australia</option>
      </select>
    </div>
    <div>
      <input type="radio" name="premium" value="500" v-model="premium" />
      Standard
      <input type="radio" name="premium" value="250" v-model="premium" /> Safe
      (+250{{ country.toUpperCase() }}, 50%)
      <input type="radio" name="premium" value="375" v-model="premium" /> Safe
      (+375{{ country.toUpperCase() }}, 75%)
    </div>
    <div>
      <h2>Your premium is {{ premium }}{{ country.toUpperCase() }}</h2>
    </div>
    <button @click="$emit('update-step', 0)">Prev</button>
    <button @click="onNext">Next</button>
  </div>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      required: true,
      default() {
        return {
          name: "",
          age: 0,
          country: "hkd",
          premium: "500",
        };
      },
    },
  },
  data() {
    return {
      name: "",
      age: 0,
      country: "hkd",
      premium: "500",
    };
  },
  watch: {
    info(newValue) {
      this.name = newValue.name;
      this.age = newValue.age;
      this.premium = newValue.premium;
      this.country = newValue.country;
    },
  },
  methods: {
    onNext() {
      this.$emit("update", this.name, this.age, this.country, this.premium);
      this.$emit("update-step", 2);
    },
  },
};
</script>