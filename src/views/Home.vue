<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="status" />
    <CountrySelect @get-country="getCountryData" :countries="countries" />
    <button
      v-if="status.Country"
      @click="clearCountryData"
      class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600"
    >
      국가 초기화
    </button>
  </main>

  <main
    class="flex justify-center items-center flex-col text-center h-80"
    v-else`
  >
    <p class="text-gray-100 text-lg mt-10 mb-6">
      Loading...
    </p>
  </main>
</template>

<script>
import DataTitle from "../components/DataTitle";
import DataBoxes from "../components/DataBoxes";
import CountrySelect from "../components/CountrySelect";

export default {
  name: "Home",

  components: { DataTitle, DataBoxes, CountrySelect },

  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      status: {},
      countries: [],
    };
  },

  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },

    getCountryData(country) {
      this.status = country;
      this.title = country.Country;
    },

    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();

      this.title = "Global";
      this.status = data.Global;
      this.loading = false;
    },
  },

  async created() {
    console.log("View Created.");
    const data = await this.fetchCovidData();
    console.log(data);

    this.dataDate = data.Date;
    this.status = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
