<template>
  <v-row justify="center">
    <v-col cols="12" lg="4" md="6" sm="8">
      <div class="generated-table">
        <v-simple-table height="300">
          <thead>
            <tr>
              <th class="text-center">ID</th>
              <th class="text-center">AD Groups</th>
              <th class="text-center">Description</th>
            </tr>
          </thead>
          <tbody class="text-center">
            <template>
              <tr v-if="checkDeviceType === this.deviceType.prem && lanId !== ''">
                <td>{{ lanId }}</td>
                <td>{{ this.deviceType.prem.group }}</td>
                <td>{{ this.deviceType.prem.name }}</td>
              </tr>
              <tr v-else-if="checkDeviceType === this.deviceType.base && lanId !== ''">
                <td>{{ lanId }}</td>
                <td>{{ this.deviceType.base.group }}</td>
                <td>{{ this.deviceType.base.name }}</td>
              </tr>
              <tr v-if="lanId !== ''">
                <td>{{ lanId }}</td>
                <td>{{ this.baseApp.group }}</td>
                <td>{{ this.baseApp.name }}</td>
              </tr>
              <tr v-for="app in selectedApps" :key="app.id">
                <td>{{ lanId }}</td>
                <td>{{ app.id }}</td>
                <td>{{ app.name }}</td>
              </tr>
            </template>
          </tbody>
        </v-simple-table>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "generated-table",
  props: {
    selectedApps: Array,
    lanId: String,
    deviceType: Object,
    baseApp: Object
  },
  computed: {
    checkDeviceType: function() {
      var deviceGroup = this.deviceType.base;
      for (var i = 0; i < this.selectedApps.length; i++) {
        if (this.selectedApps[i].delivery === "sccm") {
          deviceGroup = this.deviceType.prem;
          break;
        }
      }
      console.log(deviceGroup);
      return deviceGroup;
    }
  }
};
</script>
