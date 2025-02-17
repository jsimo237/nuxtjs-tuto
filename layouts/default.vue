
<script setup lang="ts">
   
</script>

<template>
 <div class="layout">
    
    <layout-header :title="'Default'" />

    <main>
      <nuxt-page />
    </main>

    <layout-footer />
  </div>
</template>

<style scoped>
/* Assure que la page prend toute la hauteur de l'écran */
.layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

/* Le main prend toute la place disponible pour pousser le footer en bas */
main {
  flex: 1;
  padding: 20px;
}

/* Style du header et du footer */
header {
  background: red;
  color: white;
  padding: 15px;
  text-align: center;
}

footer {
  background: #f1f1f1;
  padding: 10px;
  text-align: center;
}
</style>

