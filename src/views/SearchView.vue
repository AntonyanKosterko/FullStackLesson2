<template>
  <div>
    <v-app id="app">
      <v-container>
        <v-row>d
          <v-col v-for="(user, index) in users" :key="index" cols="6">
            <v-card hover>
              <v-list-item three-line>
                <v-list-item-avatar tile size="80">
                  <v-img
                    :src="'https://randomuser.me/api/portraits/men/' + user.id + '.jpg'"
                  ></v-img>
                </v-list-item-avatar>
                <v-list-item-content>
                  <div class="text-overline mb-4">{{ user.name }}</div>
                  <v-list-item-title class="text-h5 mb-1">
                    Headline 5
                  </v-list-item-title>
                  <v-list-item-subtitle
                    >Greyhound divisely hello coldly
                    fonwderfully</v-list-item-subtitle
                  >
                </v-list-item-content>
              </v-list-item>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </div>
</template>

<script>
//import { defineComponent } from '@vue/composition-api'
//v-for="(user, index) in users" :key="index"

export default {
  data() {
    return {
      users: {},
    };
  },

  methods: {
    getListUsers() {
      for (let i = 1; i < 10; ++i) {
        this.getUserData(i);
      }
    },
    getUserData(i) {
      this.axios
        .get("http://jsonplaceholder.typicode.com/users/" + i)
        .then((response) => {
          this.users[i - 1] = response.data;
          console.log(this.users[i - 1]);
        });
    },
  },

  mounted() {
    this.getListUsers();
  },
};
</script>

<style scoped>
</style>
