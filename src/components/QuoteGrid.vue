<template>
  <div>
    <app-quote
      v-for="(quote, index) in quotes"
      :key="index"
      :index="index"
      @quoteDeleted="deleteQuote"
    >{{quote}}</app-quote>
  </div>
</template>

<script>
import Quote from "./Quote.vue";
export default {
  components: {
    appQuote: Quote
  },
  props: ["quotes"],
  methods: {
    deleteQuote(index) {
      this.$emit("quoteDeleted", index);
    }
  }
};
</script>
