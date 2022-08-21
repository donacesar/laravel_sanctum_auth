<template>
    <div class="w-25">
        <input v-model="name" type="text" placeholder="name" class="form-control mt-3 mb-3">
        <input v-model="email" type="email" placeholder="email" class="form-control mb-3">
        <input v-model="password" type="password" placeholder="password" class="form-control mb-3">
        <input v-model="password_confirmation" type="password" placeholder="password_comfirmation" class="form-control mb-3">
        <input @click.prevent="register" type="submit" value="register" class="btn btn-primary mb-3">
    </div>
</template>

<script>
export default {
    name: "Registration",
    data() {
        return {
            name: null,
            email: null,
            password: null,
            password_confirmation: null
        }
    },

    methods: {
        register() {
            axios.get('sanctum/csrf-cookie').then(res => {
                axios.post('/register', {
                    name: this.name,
                    email: this.email,
                    password: this.password,
                    password_confirmation: this.password_confirmation
                }).then( r =>{
                    console.log(r);
                    this.$router.push('user.personal')
                })
            })
        }
    }
}
</script>

<style scoped>

</style>
