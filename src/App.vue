<template>
  <v-app>
    <v-content>
      <h1 class="text-center">AD group generator</h1>
      <v-container>
        <v-row justify="center">
          <v-col>
            <app-form :apps="apps" @send:apps="selectedAppsToObj" @send:lanId="checkLanId" />

            <generated-table
              :selectedApps="filteredAppsForTable"
              :lanId="this.userId"
              :deviceType="deviceType"
            />
          </v-col>
        </v-row>
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
    checkLanId(lanId) {
      console.log(lanId);
      this.userId = lanId;
      console.log("userid = " + this.userId);
    },
    clearData() {
      this.userId = "";
      this.filteredAppsForTable = [];
    }
  },

  data() {
    return {
      filteredAppsForTable: [],
      deviceType:
        {
          base: {
            name: "base device",
            group: "base device group",
            personalisation: "base device personlaisation"
          },
          prem: {
            name: "premium",
            group: "prem device group",
            personalisation: "prem plus device personlaisation"
          },
          premplus: {
            name: "prem plus",
            group: "prem plus device group",
            personalisation: "prem plus device personlaisation"
          }
        },
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
      ],
      userId: ""
    };
  }
};
</script>

<style  scoped>
/* h1 {
  background: red;
  margin: 0;
  padding: 0;
} */
h1 {
  color: #1976d2;
}
</style>
