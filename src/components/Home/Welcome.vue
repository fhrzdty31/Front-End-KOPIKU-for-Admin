<template>
    <div class="container col-12">
        <div class="card text-center p-2 mb-4 mx-2">
            <div class="card-body">
                <h2 class="card-title">Selamat Datang</h2>
                <h3 class="card-text text-muted">-- {{ user }} --</h3>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Welcome',
    data() {
        return {
            user: ''
        }
    },
    created() {
        this.user = localStorage.getItem('user')
    }
}
</script>

<style>

</style>