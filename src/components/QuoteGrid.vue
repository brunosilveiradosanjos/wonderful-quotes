<template>
  <div>
    <app-quote v-for="(quote, index) in quotes" :key="index">{{quote}}</app-quote>
  </div>
</template>

<script>
import Quote from "./Quote";
export default {
  components: { appQuote: Quote },
  props: ["quotes"]
};
</script>
