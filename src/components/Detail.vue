<template>
    <div>
        <h1>Detail {{ detail.nama }}</h1>
    <h4>id_produk : {{ detail.id }}</h4>
    <h4>Harga : {{ detail.harga }}</h4>
    <h4>Deskripsi : {{ detail.deskripsi }}</h4>
    <h4>id_kategori : {{ detail.id_kategori }}</h4>
    <div class="flex-container">
        <div v-for="produk in dataKategori" :key="kategori.id" class="card">
            <img :src="getimgSrc(kategori.img)" alt="Category Image" class="card-image">
            <router-link class="container" :to="{ name: 'Detail', params: { id_kategori: kategori.id }}">
            </router-link>
        </div>
    </div>
    </div>
</template>

<script>
    import { produk } from '@/assets/Produk';
import { kategori } from '../assets/Kategori';

    export default {
        props:[
            "id_produk"
        ],
        setup(props)
        {
            const getimgSrc = (imgFileName)=>{
                return '../src/assets/img/' + imgFileName + '';
            };
            const detail = produk.produk.find((item)=>{
                return item.id == props.id_produk;
            });

            return {
                detail,
                getimgSrc
            }
        }                           
    }
</script>   
<style scoped>
.flex-container {
    display: flex;
}
.card{
    /* Add shadows to create the "card" effect */
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
    margin: 10px;
    min-width: 200px;
    cursor: pointer;
}

/* On mouser-over, add a deeper shadow */
.card:hover {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
/* Add some padding inside the card container */
.container {
    padding: 2px 16px;
}
</style>