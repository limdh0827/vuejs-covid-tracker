<template>
  <div class="grid md:grid-cols-2 gap-4">
    <div
      class="s text-left hadow-md text-gray-100 border-4 px-10 py-5  rounded"
    >
      <h3 class="text-3xl font-bold mb-4">
        확진 환자
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold text-lg">
          신규:
        </span>
        {{ withComma(stats.NewConfirmed) }}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold text-lg">
          누적:
        </span>
        {{ withComma(stats.TotalConfirmed) }}
      </div>
    </div>

    <div class="shadow-md text-gray-100 border-4 px-10 py-5 text-left rounded">
      <h3 class="text-3xl  font-bold mb-4">
        사망
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold text-lg">
          신규:
        </span>
        {{ withComma(stats.NewDeaths) }}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold text-lg">
          누적:
        </span>
        {{ withComma(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
    withComma(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
