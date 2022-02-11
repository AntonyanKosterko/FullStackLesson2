<template>
  <v-app id="app">
    <NavDrawer
      :name="userData.name"
      :email="userData.email"
      :imgUrl="userData.imgUrl"
    ></NavDrawer>
    <v-main app>
      <v-header>
        <v-row no-gutters  class="green lighten-3">
          <v-col v-for="n in 1" :key="n" cols="12" sm="4">
            <h1>ReadMe</h1>
          </v-col>
        </v-row>
      </v-header>
      <v-content class="px-12 py-3">
        <v-container fluid>
          <router-view v-on:login="updateUser" :myId="myId" />
        </v-container>
      </v-content>
    </v-main>
  </v-app>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
import NavDrawer from "./components/NavDrawer.vue";
//v-for="(user, index) in users" :key="index"

export default {
  components: {
    NavDrawer,
  },

  data() {
    return {
      myId: 0,
      userData: {
        name: "Anonimus",
        email: "Anon@anonym.com",
        imgUrl: "https://socpartnerstvo.org/img/avatar_male.png",
      },
    };
  },

  methods: {
    updateUser(_userData) {
      this.userData = _userData;
      this.userData.imgUrl = "https://socpartnerstvo.org/img/avatar_male.png";
      console.log(_userData);
    },
  },

  mounted() {
    //this.getUserData();
  },
};
</script>

