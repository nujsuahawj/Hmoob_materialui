<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" persistent max-width="800px">
      <template v-slot:activator="{ on }">
        <v-btn outlined color="teal lighten-3" dark v-on="on">ເພີ່ມໂປຣແຈັກ</v-btn>
      </template>
      <v-card id="nuform">
        <v-card-title id="new">
          <span  class="">ໂປຣແຈັກໃໝ່</span>
        </v-card-title>
         <v-form class="px-3" ref="form">
        <v-card-text id="error">
           
                <v-text-field label="ຫົວຂໍ້" v-model="title" prepend-icon="folder" :rules="inputRules"></v-text-field>
                <v-textarea label="ຂໍ້ມູນ" v-model="content" prepend-icon="edit" :rules="inputRules"></v-textarea>
                <v-col cols="12" lg="6">
                 <v-menu 
          ref="menu1"
          v-model="menu1"
          :close-on-content-click="false"
          transition="scale-transition"
          offset-y
          max-width="290px"
          min-width="290px"
        >
          <template v-slot:activator="{ on }">
            <v-text-field
              v-model="dateFormatted"
              label="ວດປ"
              hint="ຮູບແບບ ດ/ວ/ປ"
              persistent-hint
              prepend-icon="event"
              @blur="date = parseDate(dateFormatted)"
              v-on="on"
            ></v-text-field>
          </template>
          <v-date-picker v-model="date" no-title @input="menu1 = false"></v-date-picker>
        </v-menu>
        </v-col>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="dialog = false">ຍົກເລີກ</v-btn>
          <v-btn color="green" text outlined @click="submit">ບັນທຶກ</v-btn>
        </v-card-actions>
         </v-form>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
    data: vm => ({
      dialog: false,
      title:'',
      content:'',
      due:null,
      date: new Date().toISOString().substr(0, 10),
      dateFormatted: vm.formatDate(new Date().toISOString().substr(0, 10)),
      menu1: false,
      inputRules: [
          v => v.length >= 3 || 'ປ້ອນຢ່າງນ້ອຍ 3 ຕົວຂື້ນໄປ' 
      ]
      
    }),
    methods: {
         formatDate (date) {
        if (!date) return null

        const [year, month, day] = date.split('-')
        return `${year}/${month}/${day}`
      },
      parseDate (date) {
        if (!date) return null

        const [year, month, day] = date.split('/')
        return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
      },
    },
    computed: {
      computedDateFormatted () {
        return this.formatDate(this.date)
      },
    },

    watch: {
      date () {
        this.dateFormatted = this.formatDate(this.date)
      },
    },


}
</script>
<style>
.description, p, span{
     font-family: 'Noto Sans Lao', sans-serif;
  }
  .overline{
    font-family: 'Noto Sans Lao', sans-serif;
  }
  .subheading{
    font-family: 'Noto Sans Lao', sans-serif;
  }
  .grey--text{
    font-family: 'Noto Sans Lao', sans-serif;
  }
  #nuform{
    font-family: 'Noto Sans Lao', sans-serif;
  }
  #new{
    font-family: 'Noto Sans Lao', sans-serif;
  }
</style>