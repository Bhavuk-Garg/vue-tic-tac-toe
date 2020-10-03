<template>
  <v-app>
    <v-main>
      <Game/>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {
    Game: ()=>import("./components/Game"),
  },

  data: () => ({
  }),
};
</script>
