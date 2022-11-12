<template>
    <div class="container text-dark mt-5">
        <div class="card position-absolute top-50 start-50 translate-middle" style="width: 32rem;">
            <div class="card-body">
                <h2 class="text-center">Register</h2>
                <form @submit.prevent="register">
                    <div class="mb-3 row">
                        <label for="email" class="col-sm-3 col-form-label my-1">Email</label>
                        <div class="col-sm-9 my-1">
                            <input v-model="email" type="text" class="form-control" id="email" placeholder="Email" required>
                        </div>
                    </div>
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
                        <button type="submit" class="btn btn-outline-success">Register</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'FormRegister',
    data() {
        return {
            username: '',
            email: '',
            pass: ''
        }
    },
    methods: {
        async register() {
            await axios.post('register', {
                username: this.username,
                email: this.email,
                password: this.pass
            });
            this.username = ''
            this.email = ''
            this.pass = ''
            this.$router.push('/login')
        }
    }
}
</script>

<style>

</style>