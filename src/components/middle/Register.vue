<template>
    <div class="register form-box">
        <div class="header">Register</div>
        <div class="body">
            <form @submit.prevent="onRegister">
                <div class="field">
                    <div class="name">
                        <label for="original">Login</label>
                    </div>
                    <div class="value">
                        <input id="original" name="original" v-model="original"/>
                    </div>
                </div>
                <div class="button-field">
                    <input type="submit" value="Register">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
                id: "",
                url: "",
                original: "",
            }
        },
        name: "Register",
        beforeCreate() {
        },
        beforeMount() {
            this.id = "";
            this.url = "";
            this.original = "";
        },
        methods: {
            onRegister: function () {
                this.$root.$emit("onRegister", 111, "aaa", this.original);
            }
        }
    }
</script>

<style scoped>

</style>
