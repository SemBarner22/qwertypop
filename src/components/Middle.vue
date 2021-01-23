<template>
    <div class="middle">
        <main>
            <Register v-if="page === 'Register'"/>
            <Result v-if="page === 'Result'" :url="url"/>
        </main>
    </div>
</template>
<script>
    import Register from './middle/Register';
    import Result from './middle/Result'

    export default {
        name: "Middle",
        props: ["url"],
        data: function () {
            return {
                page: "Register"
            }
        },
        computed: {},
        components: {
            Register,
            Result,
        }, beforeCreate() {
            this.$root.$on("onChangePage", (page, url) => {
                this.url = url;
                this.page = page;
            });
        }
    }
</script>

<style scoped>

</style>
