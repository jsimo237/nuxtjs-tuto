
<script setup lang="ts">
import type { NavigationType } from '~/types';
import type { ProductModel } from '~/types/products.type';

const navigations = reactive<NavigationType[]>([
                    {
                       label : "Liste" ,
                        link : "/products"
                     },
                  ])  

const payload = reactive<ProductModel>({
                  id : null,
                  name : null,
                  price : null,
                  description : null,
                });

const products = reactive<ProductModel[]>([]);


definePageMeta({
  layout : "products"
});


function addProduct(){
 

  /**
   *  const product = payload;
   * Vas créer un problème : du fait que products.push(product) 
   * ajoute une référence à l'objet payload dans le tableau products. 
   * Ainsi, lorsque payload est modifié, toutes les références dans products sont également mises à jour,
   *  car elles pointent vers le même objet en mémoire.
   * 
   * Solution : const product = { ...payload }
   * Cloner l'objet avant de l'ajouter.
   * Au lieu d'ajouter directement payload,
   * crée une copie indépendante de l'objet avant de l'ajouter à products.
   */

   payload.id = Date.now();
   
  const product = { ...payload };
  products.push(product)
  
  payload.id = null;
  payload.name = null;
  payload.price = null;
  payload.description = null;
}
   
</script>

<template>
  <div>

    <h3>Nouveau Produit</h3>
    <p>{{ products }}</p>
    <products-navigation :navigations="navigations" />

    <ui-form :title="`Formulaire d'ajout`">
      
      <ui-input-field 
        label="Nom du produit :"
        type="text"
        v-model="payload.name"
       />

       <ui-input-field 
          label="Prix du produit :"
          type="number"
          v-model="payload.price"
       />

       <ui-input-field 
          label="Description du produit :"
          type="textarea"
          v-model="payload.description"
       />

       <button 
       type="button"
       @click="addProduct" > 
       Ajouter
       </button>
    </ui-form>
  
  </div>

</template>

<style scoped>

</style>

