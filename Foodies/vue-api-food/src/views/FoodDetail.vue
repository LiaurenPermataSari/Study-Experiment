<template>
    <div class="fold-detail">
        <Navbar/>
        <div class="container">
            <div class="row mt-5">
                <div class="col">
                    <nav aria-label="breadcrumb">
                        <ol class="breadcrumb">
                            <li class="breadcrumb-item"><router-link class="text-dark" to="/" >Home</router-link></li>
                            <li class="breadcrumb-item"><router-link class="text-dark" to="/foods">Foods</router-link></li>
                            <li class="breadcrumb-item active" aria-current="page">Food Order Detail</li>
                        </ol>
                    </nav>
                </div>
            </div>

            <div class="row mt-3">
                <div class="col-md-6">
                    <img :src="'../assets/images/' + product.gambar " class="img-fluid shadow">
                </div>
                <div class="col-md-6">
                    <h2><strong>{{ product.nama }}</strong></h2>
                    <h4>Harga: <strong>Rp. {{ product.harga }}</strong></h4>

                    <!-- <form class="mt-4">
                        <div class="form-group">
                            <label for="jumlah_pemesanan">Jumlah Pesan</label>
                            <input type="number" class="form-control"/>
                        </div>
                        <div class="form-group">
                            <label for="keterangan">Keterangan</label>
                            <textarea class="form-control" placeholder="Keterangan : seperti pedas, sedang ..."></textarea>
                        </div>

                        <button type="submit" class="btn btn-success" @click="pemesanan"><b-icon-cart></b-icon-cart>Pesan</button>
                    </form> -->
                    <form class="mt-4" v-on:submit.prevent>
                        <div class="form-group">
                            <label for="jumlah_pemesanan">Jumlah Pesan</label>
                            <input type="number" class="form-control" v-model="pesan.jumlah_pemesanan"/>
                        </div>
                        <div class="form-group">
                            <label for="keterangan">Keterangan</label>
                            <textarea
                            v-model="pesan.keterangan"
                            class="form-control" placeholder="Keterangan : seperti pedas, sedang ..."></textarea>
                        </div>

                        <button type="submit" class="btn btn-success" @click="pemesanan"><b-icon-cart></b-icon-cart>Pesan</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import axios from 'axios'

export default {
    name: 'FoodDetail',
    components: {
        Navbar,
    },
    data(){
        return {
            product: {},
            pesan: {},
        }
    },
    methods: {
        setProducts(data){
            this.product = data
        },
        pemesanan(){
            this.pesan.products = this.product
            axios
            .post("http://localhost:3000/keranjangs", this.pesan)
            .then(() => {
                this.$toast.success('Profile saved.', {
                    type: 'success',
                    position: 'top-right',
                    duration: 3000,
                    dismissible: true
                })
            })
            .catch((err) => console.log(err))
        },
    },
    mounted(){
        axios
        .get("http://localhost:3000/products/" + this.$route.params.id)
        .then((response) => this.setProducts(response.data))
        .catch((error) => console.log(error))
    }
}
</script>