<template>
    <div class="container text-dark mt-5">
        <div class="card position-absolute top-50 start-50 translate-middle" style="width: 32rem;">
            <div class="card-body">
                <h2 class="text-center">LogIn</h2>
                <form @submit.prevent="login">
                    <div class="mb-3 row">
                        <label for="username" class="col-sm-3 col-form-label my-1">Username</label>
                        <div class="col-sm-9 my-1">
                            <input v-model="username" type="text" class="form-control" id="username" placeholder="Username" required>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label for="pass" class="col-sm-3 col-form-label my-1">Password</label>
                        <div class="col-sm-9 my-1">
                            <input v-model="pass" type="password" class="form-control" id="pass" placeholder="Password" required>
                        </div>
                    </div>
                    <div class="text-center">
                        <button type="submit" class="btn btn-outline-success">Login</button>
                        <h6 class="mt-3">Tidak ada Akun? <router-link to="/register">Register</router-link></h6>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'FormLogin',
    data() {
        return {
            username: '',
            pass: '',
        }
    },
    methods: {
        async login() {
            try {
                var response = await axios.post('login', {
                    username: this.username,
                    password: this.pass
                });
                localStorage.setItem('token', response.data);
                localStorage.setItem('user', this.username)
                localStorage.setItem('status', true);
                this.$emit('authenticathed', true);
                location.href="/"
            } catch (e) {
                alert('Password atau Username Salah')
                console.log(e);
            }
        }
    },
    mounted() {
        if(localStorage.getItem('status')) {
        this.$router.replace({name:'home'})
        }
    }
}
</script>

<style>

</style>