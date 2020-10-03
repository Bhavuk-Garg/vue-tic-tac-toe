<template>
  <div class="d-flex justify-center text-center">
    <v-sheet elevation="3" :color="color" min-width="300" class="py-5" dark>
      <slot></slot>
    </v-sheet>
  </div>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      default: "blue",
    },
  },
  computed: {
    style() {
      return "background-color: " + this.color;
    },
  },
};
</script>

<style></style>
