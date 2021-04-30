<template>
  <select
    @change="onCountryChange()"
    v-model="selected"
    class="form-select border-none bg-gray-100 mt-10 block w-full p-3 rounded"
  >
    <option value="0">Select Country</option>
    <option
      v-for="country in countries"
      :value="country.ID"
      :key="country.ID"
      >{{ country.Country }}</option
    >
  </select>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },

  methods: {
    onCountryChange() {
      const country = this.countries.find((item) => item.ID === this.selected);

      console.log(country);

      this.$emit("get-country", country);
    },
  },
};
</script>
