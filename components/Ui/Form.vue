
<script setup lang="ts">

type PropsType = {
                title? : string
              }

const props = withDefaults(
                defineProps<PropsType>(),
              {
                title : "Titre"
              }
            )

</script>

<template>
    <form>
      <h3>{{ title }}</h3>
      <slot />
   </form>
</template>

<style scoped>

</style>

