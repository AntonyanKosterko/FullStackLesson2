<template>
  <v-app id="app">
    <v-navigation-drawer
      app
      color="green"
      dark
      expand-on-hover
      hide-overlay
      permanent
      right
    >
      <v-list nav dense>

        <v-list-item link>
          <v-list-item-avatar>
            <v-img
              src="https://randomuser.me/api/portraits/women/85.jpg"
            ></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="text-h6 font-weight-black">
              Sandra Adams
            </v-list-item-title>
            <v-list-item-subtitle>sandra_a88@gmail.com</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider class="my-3"></v-divider>

      <v-list shaped nav dense>
        <v-list-item link to="/">
          <v-list-item-icon>
            <v-icon>mdi-home-outline</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Главная</v-list-item-title>
        </v-list-item>
        <v-list-item link to="/profile">
          <v-list-item-icon>
            <v-icon>mdi-account-multiple</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Мой профиль</v-list-item-title>
        </v-list-item>
        <v-list-item link to="/search">
          <v-list-item-icon>
            <v-icon>mdi-star</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Найти друзей</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main app>
      <v-content class="px-12 py-3">
        <v-container fluid>
          <router-view v-on:login="updateUser"/>
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
