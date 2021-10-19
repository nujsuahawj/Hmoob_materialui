<template>
  <v-app>
  <Navbar/>
    <v-content class="ma-4">
      <router-view></router-view>
    </v-content>
     <Footer/>
  </v-app>
 
</template>

<script>

import Navbar from '@/components/Navbar'
import Footer from '@/components/Footer'
export default {
  name: 'App',

  components: {
   Navbar,
   Footer,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
@font-face {
  font-family: "Noto Sans Lao";
  src: local("Noto Sans Lao"),
   url(./assets/fonts/NotoSansLao-VariableFont_wdth,wght.ttf) format("truetype");
}
/* @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Lao:wght@100&display=swap'); */
</style>
