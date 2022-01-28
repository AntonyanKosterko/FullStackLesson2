<template>
    <div>
        <v-row class="text-left">
            <v-col cols="10">
                <h1 class="green--text text--darken-2">
                    <v-icon large color="green darken-2">mdi-account-outline</v-icon>
                    {{ userData.name }}
                </h1>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="2">
                <img :src="'https://randomuser.me/api/portraits/men/' + userId + '.jpg'" style="max-width: 100%">
            </v-col>
            <v-col cols="10" class="text-left">
                <p>
                    Веб-сайт: <a href="" target="_blank">{{ userData.website }}</a>
                </p>
                <p>
                    E-mail: <a href="">{{ userData.email }}</a>
                </p>
                <p>
                    Город: {{ userData.address.city }}
                </p>
                <p>
                    Место работы: {{ userData.company.name }}
                </p>
            </v-col>
        </v-row>

        ОСТАЛЬНОЕ СОДЕРЖИМОЕ СТРАНИЦЫ
    </div>
</template>

<script>
//import { defineComponent } from '@vue/composition-api'

export default({
    data(){
        return{
            userId: 0,
            user_posts: [],
            userData: {},
        }
    },

    methods:{
        getUserData(){
            this.axios.get('http://jsonplaceholder.typicode.com/users/' + this.userId)
            .then((response) => {
                this.userData = response.data;
                console.log(this.userId);
                console.log(this.userData);
            });
        },

        getUserPosts(){
            this.axios.get('http://jsonplaceholder.typicode.com/posts?userId=' + this.userId)
            .then((response) => {
                this.user_posts = response.data;
            });
        },

        getData(){
            this.userId = this.$route.params.id;
            this.getUserData();
            this.getUserPosts();
        }
    },

    mounted(){
        this.getData();
    },

    watch:{
        $route(){
            this.getData();
        }
    },
})
</script>
