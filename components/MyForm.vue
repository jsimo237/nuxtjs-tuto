
<script setup lang="ts">

type PayloadRegisterType = {
    name : string | null,
    email : string | null,
    phone : number | null,
}

const titleForm = ref<string>("Formulaire d'incription");


const payload = reactive<PayloadRegisterType>({
                    name : null,
                    email : null,
                    phone : null,
                })
     
     
 function register(){

    console.log("payload => ",payload);
 }    
</script>

<template>
    <UiForm :title="titleForm">

       <div style="margin-bottom: 20px;">
        {{ payload }}
       </div>
        
        <UiInputField 
            v-model="payload.name"
            :label="`Nom Complet`" 
            :type="'text'"/>

        <UiInputField 
             v-model="payload.email"
            :label="`Email`" 
            :type="'email'"/>

        <UiInputField 
         v-model="payload.phone"
         :label="`Téléphone`"
         :type="'number'" />

        <div style="margin-bottom: 10px;">
             <button 
               @click="register"
                 type="button">
             Valider 
            </button>
        </div>
    </UiForm>

</template>

<style scoped>

</style>

