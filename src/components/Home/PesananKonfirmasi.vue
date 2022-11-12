<template>
    <div class="container col-lg-6">
        <div class="card text-center p-2 mb-4 mx-2">
            <div class="card-body">
                <h2 class="card-title">Daftar Pesanan Konfirmasi</h2>
                <hr>
                <table class="table align-middle mt">
                    <thead>
                        <tr>
                            <th scope="col">Nama</th>
                            <th scope="col">Status</th>
                            <th scope="col">Aksi</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="pesan in pesanan" :key="pesan.id">
                            <td>{{ pesan.nama }}</td>
                            <td>
                                <span class="badge rounded-pill text-light bg-info"><i class="bi bi-check-circle-fill"></i> Menunggu Konfirmasi</span>
                            </td>
                            <td>
                                <button v-on:click="konfirmasi(pesan.id)" class="btn btn-outline-info"><i class="bi bi-check-circle-fill"></i> Konfirmasi</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'PesananKonfirmasi',
    data() {
        return {
            pesanan: []
        }
    },
    created() {
        this.getAll()
    },
    methods: {
        async getAll() {
            var header = { Authorization: `Bearer ${(localStorage.getItem('token')).toString()}`};
            try {
                var response = await axios.get('pesananAdmin/k', {headers: header})
                this.pesanan = response.data
            } catch (e) {
                console.log(e.response.data.messages.error);
            }
        },
        async konfirmasi(id) {
            try {
                var response = await axios.get(`pesanan/${id}`);
                await axios.put(`pesanan/${id}`, {
                    nama: response.data.nama,
                    pesanan: response.data.pesanan,
                    jumlah: response.data.jumlah,
                    harga: response.data.harga,
                    status: 'pembayaran'
                });
                this.getAll()
            } catch (e) {
                console.log(e);
            }
        }
    }
}
</script>

<style>

</style>