
<script setup lang="ts">

// Type pour propriétés
type PropsType = {
                modelValue : any,
                label : string,
                type? : string,
                rows? : number,
                cols? : number,
              }


// Definitions des Evenements du composant
const emit = defineEmits(['update:modelValue'])

// Definitions des propriété du composant
const props = withDefaults(
                defineProps<PropsType>(),
              {
                type : "text",
                rows : 2,
                cols : 15,
              }
            )


 /**
  * 1er cas de définition d'une variable capable de binder (v-model)
  *  ce composant depuis l'extérieur          
  */ 
const VModel1 = computed<any>({
                get : ()=> props.modelValue,
                set : (value : any)=> {
                   emit('update:modelValue',value)
                },
              })


 /**
  * 2e cas de définition d'une variable capable de binder (v-model)
  *  ce composant depuis l'extérieur          
  */             
 const VModel2 = ref<any>(props.modelValue)  
 
 watch (
  VModel2,
  (newVal)=> {
    emit('update:modelValue',newVal)
  }
 )


</script>

<template>
    <div style="margin-bottom: 10px;">
        <label for="name" style="margin-right: 10px;">
          {{ label }}
        </label>
        <input
         v-model="VModel1" 
         :type="type" 
         v-if="type !== 'textarea'">
      
        <textarea v-else 
          v-model="VModel1"
          :rows="rows"
          :cols="cols"
        />

      
    </div>
</template>

<style scoped>

</style>

