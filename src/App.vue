<template>
  <div>
    <div v-if="authenticathed">
      <nav class="navbar fixed-bottom navbar-light bg-light">
        <div class="container-fluid mx-2">
          <h1 class="navbar-brand text mx-4 my-2">Admin - <i class="bi bi-cup-hot"></i> KopiKu</h1>
          <a v-on:click="logout" type="button" class="btn btn-outline-dark">LogOut</a>
        </div>
      </nav>
      <br>
      <router-view />
      <br><br>
    </div>
    <div v-else>
      <br><br>
      <router-view @authenticated="setAuthenticated"></router-view>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      authenticathed: localStorage.getItem('status'),
    }
  },
  methods: {
    async logout() {
      localStorage.clear()
      location.href="/login"
    },
    async setAuthenticated(status) {
      this.authenticathed=status
    }
  }
}
</script>

<style>
@import '~bootstrap';
@import '~bootstrap/dist/css/bootstrap.css';
@import '~bootstrap-icons/font/bootstrap-icons.css';
</style>
