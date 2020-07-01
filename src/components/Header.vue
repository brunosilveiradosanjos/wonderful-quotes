<template>
  <div>
    <v-progress-linear :value="value" height="25">
      <strong>{{ value }} / {{10*maxQuotes }}</strong>
    </v-progress-linear>
  </div>
</template>

<script>
export default {
  props: ["quotes", "maxQuotes"],
  computed: {
    value() {
      return 10 * this.quotes.length;
    }
  }
};
</script>