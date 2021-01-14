<template>
  <v-app>
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    //
  }),
};
</script>

<style lang="scss" scoped>
.v-application {
  background: #fafafa !important;

  @media screen and (max-width: 600px) {
    background: #fff !important;
  }
}
</style>
