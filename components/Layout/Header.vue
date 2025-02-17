
<script setup lang="ts">

type PropsType = {
                title? : string,
              }
const props = withDefaults(
        defineProps<PropsType>(),
            {
                title : "EXERCICES GESTION DES PRODUITS"
            }
            )
</script>

<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
</template>

<style scoped>

</style>

