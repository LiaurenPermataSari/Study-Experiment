<template>
    <div class="card card-product">
        <img :src="'assets/images/' + product.gambar" class="card-img-top" alt="...">
        <div class="card-body">
        <h5 class="card-title">{{ product.nama }}</h5>
        <p class="card-text">{{ product.harga }}</p>
        <router-link :to="'/foods/' + product.id" class="btn btn-success"><b-icon-cart></b-icon-cart>Pesan</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardProduct',
    props: ['product'],
}
</script>