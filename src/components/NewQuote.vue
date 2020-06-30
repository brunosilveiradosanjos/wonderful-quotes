<template>
  <div class="mx-6 my-4 pa-4">
    <v-form>
      <v-row>
        <v-col>
          <v-textarea
            v-model="quote"
            :error-messages="quoteErrors"
            :counter="200"
            label="Quotes:"
            required
            auto-grow
            filled
            @input="$v.quote.$touch()"
            @blur="$v.quote.$touch()"
          ></v-textarea>
        </v-col>
      </v-row>
      <v-row align="center">
        <v-btn class="mx-auto primary" @click.prevent="createNew">Add Quote</v-btn>
      </v-row>
    </v-form>
  </div>
</template>

<script>
import { validationMixin } from "../../node_modules/vuelidate";

import {
  required,
  maxLength,
  minLength
} from "../../node_modules/vuelidate/lib/validators";

export default {
  data() {
    return {
      quote: null
    };
  },
  mixins: [validationMixin],
  validations: {
    quote: { required, maxLength: maxLength(200), minLength: minLength(5) }
  },
  computed: {
    quoteErrors() {
      const errors = [];
      if (!this.$v.quote.$dirty) return errors;
      !this.$v.quote.required && errors.push("Obrigatório");
      !this.$v.quote.maxLength && errors.push("Máximo 200 caracteres");
      !this.$v.quote.minLength && errors.push("Mínimo 5 caracteres");
      return errors;
    }
  },
  methods: {
    createNew() {
      this.$v.$touch();
      if (this.$v.$invalid) {
        console.log("ERROR!");
        this.submitStatus = "ERROR";
      } else {
        console.log("PENDING!");
        // do your submit logic here
        this.submitStatus = "PENDING";
        setTimeout(() => {
          console.log("OK!");
          this.submitStatus = "OK";
          this.$emit("quoteAdded", this.quote);
          this.quote = "";
        }, 500);
      }
    }
  }
};
</script>

<style scoped>
div {
  font-size: 25px;
}
</style>