<template>
    <!--suppress HtmlUnknownTag -->
    <body id="app">
    <Middle :url="url"/>
    </body>
</template>

<script>
    import Middle from './components/Middle'
    import axios from 'axios'

    export default {
        name: 'app',
        data: function () {
            return {
                url: null
            }
        },
        components: {
            Middle,
        }, beforeCreate() {
            // axios.get("/api/1/posts").then(posts => this.posts = posts["data"]);
            // axios.get("/api/1/users").then(users => this.users = users["data"]);

            //     axios.get("/api/1/users/authorized").then(response => {
            //         this.user = response.data;
            //         if (enter) {
            //             this.$root.$emit("onEnterSuccess");
            //         }
            //     });
            // });

            // this.$root.$on("onEnter", (login, password) => {
            //     axios.post("/api/1/jwt", {
            //         login: login,
            //         password: password
            //     }).then(response => {
            //         localStorage.setItem("jwt", response.data);
            //         this.$root.$emit("onJwt", response.data, true);
            //     }).catch(error => {
            //         this.$root.$emit("onEnterValidationError", error.response.data);
            //     });
            // });

            this.$root.$on("onRegister", (id, url, original) => {
                axios.post("/api/create", {
                    original
                    // eslint-disable-next-line no-unused-vars
                }).then((response) => {
                        this.url = response.data;
                        this.$root.$emit("onChangePage", 'Result');
                    })
                //     // axios.get("/api/1/users").then(users => this.users = users["data"]);
                // }).catch(error => {
                //     this.$root.$emit("onRegisterValidationError", error.response.data);
                // })
            });

            // this.$root.$on("onAddPost", (user, title, text) => {
            //     if (!this.user) {
            //         this.$root.$emit("onAddPostValidationError", 'You are not authorized');
            //     }
            //     axios.post("/api/1/posts", {
            //         user,
            //         title,
            //         text
            //     }).then(() => {
            //         this.$root.$emit("onChangePage", 'Index');
            //         axios.get("/api/1/posts").then(posts => this.posts = posts["data"]);
            //     }).catch(error => {
            //         this.$root.$emit("onAddPostValidationError", error.response.data);
            //     })
            // });
        }, beforeMount() {
        }
    }
</script>

<style>
</style>
