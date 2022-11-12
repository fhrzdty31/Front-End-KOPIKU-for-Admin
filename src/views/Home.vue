<template>
    <div class="container text-dark mt-2">
        <div class="row">
            <Welcome />
            <PesananKonfirmasi />
            <PesananProses />
        </div>
    </div>
</template>
  
<script>
import Welcome from '@/components/Home/Welcome.vue'
import PesananKonfirmasi from '@/components/Home/PesananKonfirmasi.vue'
import PesananProses from '@/components/Home/PesananProses.vue'
  
export default {
    nameL: 'Home',
    components: {
        Welcome,
        PesananKonfirmasi,
        PesananProses
    },
    mounted() {
        if(!localStorage.getItem('status')) {
        this.$router.replace({name:'login'})
        }
    }
  }
</script>
  
<style>

</style>