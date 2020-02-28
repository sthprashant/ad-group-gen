<template>
  <v-app>
    <v-content>
      <v-row>
        <v-col v-model="selectedApps" cols="12" class="text-center">
          {{selectedAppsForm}}
        </v-col>
        <v-col cols="12" class="text-center">
          <h1>Test</h1>
        </v-col>
        <v-col cols="12">
          <app-form
            :apps="apps"
            :selectedApps="selectedApps"
            @send:apps="selectedAppsToObj"
          />
        </v-col>
        <v-col cols="12">
          <generated-table />
        </v-col>
      </v-row>
    </v-content>
  </v-app>
</template>

<script>
import AppForm from "@/components/AppForm.vue";
import GeneratedTable from "@/components/GeneratedTable.vue";
export default {
  name: "App",

  components: {
    AppForm,
    GeneratedTable
  },
  methods: {
    selectedAppsToObj(selectedApps){
      this.selectedAppsForm = [...this.selectedAppsForm,selectedApps[selectedApps.length -1]];
      
    },
  },
  data: () => ({
    selectedAppsForm: [],
    filteredAppsForTable: [],
    apps: [
      {
        id: "AVC-AP2-QS-APPV-ACROBATPRO_LAD",
        name: "Acrobat Pro",
        delivery: "appv"
      },
      {
        id: "AVC-AP2-QS-CORE-BARSPROD_LAD",
        name: "BARS Production",
        delivery: "sccm"
      },
      {
        id: "AVC-AP2-QS-APPV-SAS_LAD",
        name: "SAS",
        delivery: "appv"
      },
      {
        id: "AVC-AP2-QS-CORE-RSAT_LAD",
        name: "Active Directory",
        delivery: "sccm"
      },
      {
        id: "AVC-AP2-QS-CORE-LINKSPROD_LAD",
        name: "LINKS Production",
        delivery: "sccm"
      }
    ]
  })
};
</script>
