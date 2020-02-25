<template>
  <v-app>
    <!-- <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar> -->

    <v-content>
      <v-row class="text-center">
        <v-col cols="12">
        <h1>AD Group Generator for AVC 2</h1>
      </v-col>
      <v-col>
        <entry-form :apps="apps"/>
      </v-col>
      </v-row>
      
    </v-content>
  </v-app>
</template>

<script>
import EntryForm from '@/components/EntryForm.vue';
export default {
  name: 'App',

  components: {
    EntryForm,
  },

  data: () => ({
    apps:[{
            id: "AVC-AP2-QS-APPV-ACROBATPRO_LAD",
            name:"Acrobat Pro",
            delivery:"appv"
          },
          {
            id: "AVC-AP2-QS-CORE-BARSPROD_LAD",
            name:"BARS Production",
            delivery:"sccm"
          },
          {
            id: "AVC-AP2-QS-APPV-SAS_LAD",
            name:"SAS",
            delivery:"appv"
          },
          {
            id: "AVC-AP2-QS-CORE-RSAT_LAD",
            name:"Active Directory",
            delivery:"sccm"
          },
          {
            id: "AVC-AP2-QS-CORE-LINKSPROD_LAD",
            name:"LINKS Production",
            delivery:"sccm"
          },]
  }),
};
</script>
