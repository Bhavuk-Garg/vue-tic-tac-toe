<template>
  <v-container class="mt-15">
    <div v-for="row in 3" :key="row" class="d-flex justify-center">
      <Square v-for="col in 3" :key="col" :value="findValue(row, col)"
            @click="$emit('click',findIndex(row,col))" 
            :winner="!!winner"/>
    </div>
  </v-container>
</template>

<script>
export default {
  props: ["squares","winner"],
  components: {
    Square: () => import("./Square"),
  },
  methods: {
      findIndex(row,col){
          return (row - 1) * 3 + (col - 1);
      },
    findValue(row, col) {
      let index = this.findIndex(row,col);
      if (this.squares[index] == null) return "";
      return this.squares[index];
    },
  },
};
</script>

<style></style>
