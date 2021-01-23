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

            this.$root.$on("onRegister", (id, url, original) => {
                axios.post("/api/create", {
                    original
                    // eslint-disable-next-line no-unused-vars
                }).then((response) => {
                        this.url = response.data;
                        this.$root.$emit("onChangePage", 'Result');
                    })
            });

        }, beforeMount() {
        }
    }
</script>

<style>
</style>
