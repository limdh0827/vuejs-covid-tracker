<template>
  <div class="text-left  text-gray-100 mb-5 p-5">
    <div class="text-lg mt-4 ">{{ timestamp }}</div>
    <h2 class="text-5xl font-bold">{{ text }}</h2>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "DataTitle",
  props: ["text", "dataDate"],
  computed: {
    timestamp: function() {
      return moment(this.dataDate).format("MMMM Do YYYY, h:mm:ss a");
    },
  },
};
</script>
