<template>
   <nav>
       <v-app-bar  color="blue darken-2" dark app >
           <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
           <v-toolbar-title class="text-uppercase ">
               <span class="font-weight-light">ໜ້າ</span>
               <span>ຫຼັກ</span>
           </v-toolbar-title>
           <v-spacer></v-spacer>
           <v-menu offset-y>
      <template v-slot:activator="{ on }">
        <v-btn
          text
          v-on="on"
        >
          <v-icon left>expand_more</v-icon>
            <span>ເມນູ</span>
        </v-btn>
      </template>
      <v-list flat>
        <v-list-item v-for="link in links"  :key="link.text" router :to="link.route" active-class="border">
          <v-list-item-title >{{link.text}}</v-list-item-title>
        </v-list-item>
      </v-list>
            </v-menu>
            <v-btn text>
                <span>ອອກຈາກລະບົບ</span>
                <v-icon right>exit_to_app</v-icon>
             </v-btn>
       </v-app-bar>
      <v-navigation-drawer  v-model="drawer" dark app class="blue darken-2">
          <v-layout column align-center>
               <v-flex class="mt-5"> 
                    <v-avatar size="100">
                            <img src="/img1.png" alt="">
                    </v-avatar>
                    <p class="white--text subheading mt-1 text-center">ຊື່ ຂອງທ່ານ</p>
               </v-flex>
               <v-flex class="mt-4 mb-4">
                <Popup />
               </v-flex>
          </v-layout>
          <v-list flat id="navpro">
              <v-list-item v-for="link in links"  :key="link.text" router :to="link.route" active-class="border">
                  <v-list-item-action>
                     <v-icon >{{link.icon}}</v-icon>
                  </v-list-item-action>
                  <v-list-item-content >
                      <v-list-item-title >{{link.text}}</v-list-item-title>
                  </v-list-item-content>
              </v-list-item>
          </v-list>
      </v-navigation-drawer>
   </nav>
</template>
<script>
import Popup from './Popup.vue'
export default {
   data: () => ({
      drawer: true,
      links :[
          {icon: 'dashboard', text:'Dashboard', route: '/'},
          {icon: 'folder', text:'ໂປຣແຈັກ', route: '/projects'},
          {icon: 'person', text:'ທີມ', route: '/team'}
      ]
     
    }),
    components: {
    Popup
  },

   
}
</script>
<style scoped>
.border {
  border-left: 4px solid #0ba518;
}
.description, p, span{
     font-family: 'Noto Sans Lao', sans-serif;
  }
  #navpro{
    font-family: 'Noto Sans Lao', sans-serif;
  }
</style>
