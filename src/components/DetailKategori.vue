<template>
    <div>
        <h1>{{ detail.nama }}</h1>
    <div class="flex-container">
        <div v-for="produk in dataProduk" :key="produk.id" class="card">
            <img :src="getimgSrc(produk.img)" alt="Category Image" class="card-image">
            <router-link class="container" :to="{ name: 'Detail', params: { id_produk: produk.id }}">
                <h4>{{ produk.nama }}</h4>
            </router-link>
        </div>
    </div>
    </div>
</template>

<script>
import { kategori } from '@/assets/Kategori';
    import { produk } from '@/assets/Produk';

    export default {
        props:[
            "id_kategori"
        ],
        setup(props)
        {
            const getimgSrc = (imgFileName)=>{
                return '../src/assets/img/' + imgFileName + '';
            };
            const detail = kategori.kategori.find((item)=>{
                return item.id == props.id_kategori;
            });

            const dataProduk = produk.produk.filter(e=>{
                return detail.id == e.id_kategori;
            });

            return {
                detail,
                dataProduk,
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