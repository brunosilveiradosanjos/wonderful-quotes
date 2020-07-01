<template>
  <!--  -->
  <v-card @click="deleteQuote(index)" color="grey lighten-4" class="mx-6 my-4 pa-4">
    <v-hover v-slot:default="{ hover }">
      <v-row>
        <slot></slot>
        <v-expand-transition>
          <div
            v-if="hover"
            class="d-flex transition-fast-in-fast-out deep-orange accent-1 v-card--reveal display-3 white--text"
            style="height: 100%;"
          ></div>
        </v-expand-transition>
      </v-row>
    </v-hover>
  </v-card>
  <!--  -->
</template>

<script>
export default {
  props: ["index"],
  methods: {
    deleteQuote(index) {
      this.$emit("quoteDeleted", index);
    }
  }
};
</script>

<style scoped>
.row {
  font-family: "Arizonia", cursive;
  font-size: 30px;
  color: #6e6e6e;
  justify-content: center;
  align-items: center;
}
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}
</style>