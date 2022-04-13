<template>
  <div id="app">
    <Step1 v-if="step === 0" @update-step="updateStep" />
    <Step2
      v-else-if="step === 1"
      :info="info"
      @update="updateInfo"
      @update-step="updateStep"
    />
    <Step3 v-else @update-step="updateStep" />
  </div>
</template>

<script>
import Step1 from "./components/Step1";
import Step2 from "./components/Step2";
import Step3 from "./components/Step3";

export default {
  name: "App",
  components: {
    Step1,
    Step2,
    Step3,
  },
  data() {
    return {
      step: 0,
      info: {
        name: "",
        age: 0,
        country: "hkd",
        premium: "500",
      },
    };
  },
  provide() {
    return {
      info: this.info,
    };
  },
  methods: {
    goNextStep() {
      if (this.step < 2) {
        this.step = this.step + 1;
      }
    },

    goPrevStep() {
      if (this.step > 0) {
        this.step = this.step - 1;
      }
    },

    updateStep(val) {
      this.step = val;
    },

    updateInfo(name, age, country, premium) {
      this.info.name = name;
      this.info.age = age;
      this.info.country = country;
      this.info.premium = premium;
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
