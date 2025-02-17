
<script setup lang="ts">
import type { NavigationType } from '~/types';
import type { ProductModel } from '~/types/products.type';


const products = reactive<ProductModel[]>([
     { id : 1 , name : "Produit 1", price : 30},
     { id : 2 , name : "Produit 2", price : 40},
  ]);

const navigations = reactive<NavigationType[]>([
                    {
                       label : "Ajouter" ,
                        link : "/products/create"
                     },
                  ])  

definePageMeta({
  layout : "products"
});
   
</script>

<template>
  <div>

    <h3>Liste des produits</h3>
    <products-navigation :navigations="navigations" />
  

    <table border="1px">
      <thead>
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>Price</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(product,i) in products" :key="product.id">
          <td>{{ product.id }}</td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
        </tr>
      </tbody>
    </table>
  </div>

</template>

<style scoped>

</style>

