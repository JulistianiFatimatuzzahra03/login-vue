<template>
    <div>
     <center>
     <h1>Produk</h1>
     </center>
     <div class="flex-container">
       <div v-for="kategori in state" :key="kategori.id" class="card">
         <img :src="getimgSrc(kategori.img)" alt="Category Image" class="card-image" style="width: 300px; height: 300;">
         <router-link class="container" :to="{name: 'DetailKategori', params: { id_kategori: kategori.id}}">
           <h4>{{ kategori.namakategori }}</h4>
         </router-link>
       </div>
     </div>
    </div>
   </template>
   
   <script>
     import {
       onMounted , reactive
     } from 'vue'
     import { kategori } from '../assets/Kategori';
   
     export default {
       setup(props, context)
       {
         const state = reactive(kategori.kategori);
   
         const getimgSrc = (imgFileName) => {
           return '../src/assets/img/' + imgFileName + ''; 
         };
   
         onMounted(() => {
           context.emit("id-menu", 4)
         });
         return {
           state,
           getimgSrc
         }
       }
     }
   </script>
   
   <style scoped>
     .flex-container{
       display: flex;
       flex-wrap: wrap;
     }
   .card{
     box-shadow: 0 1px 5px 0 rgba(0, 0, 0, 2);
     transition: 0.3s;
     margin: 10px;
     min-width: 200px;
     cursor: pointer;
     text-align: center;
   }
   .container{
     padding: 2px 16px;
   }
   
   img{
     width: 200px;
     height: 160px;
   }
   </style>