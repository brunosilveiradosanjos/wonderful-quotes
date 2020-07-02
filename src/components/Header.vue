<template>
  <div class="mx-6 mt-2 pa-4">
    <v-progress-linear :value="value" height="25">
      <strong>{{ value }} / 100</strong>
    </v-progress-linear>
  </div>
</template>

<script>
export default {
  props: ["quotes", "maxQuotes"],
  computed: {
    value() {
      return (100 / this.maxQuotes) * this.quotes.length;
    }
  }
};
</script>