<template>
  <div>
    <v-stepper v-model="e1" alt-labels>
      <template>
        <v-stepper-header>
          <template v-for="n in steps">
            <v-stepper-step
              :key="`${n}-step`"
              :complete="e1 > n"
              :step="n"
              :editable="editable"
            >Step {{ n }}</v-stepper-step>

            <v-divider v-if="n !== steps" :key="n"></v-divider>
          </template>
        </v-stepper-header>

        <v-stepper-items>
          <v-stepper-content v-for="n in steps" :key="`${n}-content`" :step="n">
            <v-card class="mb-12" color="grey lighten-1" min-height="348px"><DatabaseSelect/></v-card>

            <v-btn color="primary" @click="nextStep(n)">Continue</v-btn>

            <v-btn text>RESET TO DEFAULTS</v-btn>
          </v-stepper-content>
        </v-stepper-items>
      </template>
    </v-stepper>
  </div>
</template>

<script>
import DatabaseSelect from "./DatabaseSelect"
export default {
  data() {
    return {
      e1: 1,
      steps: 7,
      altLabels: true,
      editable: true,
    };
  },
  components: {
    DatabaseSelect
  },

  watch: {
    steps(val) {
      if (this.e1 > val) {
        this.e1 = val;
      }
    },
    vertical() {
      this.e1 = 2;
      requestAnimationFrame(() => (this.e1 = 1)); // Workarounds
    },
  },

  methods: {
    onInput(val) {
      this.steps = parseInt(val);
    },
    nextStep(n) {
      if (n === this.steps) {
        this.e1 = 1;
      } else {
        this.e1 = n + 1;
      }
    },
  },
};
</script>
