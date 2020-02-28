<template>
  <v-app>
    <v-content>
      <h1 class="text-center">AD group generator</h1>
      <v-container>
        <!-- <v-col v-model="selectedApps" cols="12" class="text-center">
          <ul v-for="(app,i) in filteredAppsForTable" :key="i">
            <li>{{app}}</li>
          </ul>
          <p>{{filteredAppsForTable.length}}</p>
        </v-col>-->
          <app-form :apps="apps" @send:apps="selectedAppsToObj" />
          <generated-table :selectedApps="filteredAppsForTable" />
      </v-container>
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
    selectedAppsToObj(selectedApps) {
      this.filteredAppsForTable = [];
      for (var i = 0; i < selectedApps.length; i++) {
        for (var j = 0; j < this.apps.length; j++) {
          if (selectedApps[i] === this.apps[j].id) {
            this.filteredAppsForTable = [
              ...this.filteredAppsForTable,
              this.apps[j]
            ];
            console.log(this.filteredAppsForTable);
          }
        }
      }
      //}
    },
    returnLastSelected(selectedApps) {
      selectedApps.map(() => {
        return "test";
      });
    }
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

<style  scoped>
h1{
  background:red;
  margin: 0;
  padding: 0;
}
</style>
