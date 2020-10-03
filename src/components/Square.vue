<template>
  <v-btn
    :outlined="!!value"
    tile
    min-height="100"
    min-width="100"
    class="bordered display-2"
    :color="findColor"
    :disabled="winner"
    @click="$emit('click')"
  >
    {{ value }}
  </v-btn>
</template>

<script>
export default {
  props: {
    value:String,
    winner: Boolean
  },
  computed: {
    findColor() {
      if (this.value == "X") return "purple";
      else if (this.value == "O") return "orange";
      return "gray";
    },
  },
};
</script>

<style scoped>
.bordered {
  border: 2px solid black;
}
</style>
