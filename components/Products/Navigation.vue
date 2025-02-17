
<script setup lang="ts">
import type { NavigationType } from '~/types';

   type PropsType = {
      navigations : NavigationType[]
   }

   const props = defineProps<PropsType>()
</script>

<template>
 <div style="margin-bottom: 10px;">
      <nuxt-link 
        v-for="(navigation ,i) in navigations"
        :key="i"
        :to="navigation.link">
        {{ navigation.label }}
      </nuxt-link>
    </div>
</template>

<style scoped>

</style>

