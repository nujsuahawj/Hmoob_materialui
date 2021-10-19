<template>
  <v-footer
    dark
    padless
    app
    inset
    
  >
    <v-card
      class="flex"
      flat
      tile
      color="#1976D2"
      :elevation="10"
    >

      <v-card-text class="py-2 white--text text-center">
        {{ new Date().getFullYear() }} — <strong>Material UI by jack sainther</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<style>
.description, p, span, strong{
     font-family: 'Noto Sans Lao', sans-serif;
  }
</style>
