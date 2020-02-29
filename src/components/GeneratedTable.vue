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
              <tr>
                <td>{{lanId}}</td>
                <td v-if="app.id === 'sccm'"></td>
                <td>test</td>
              </tr>
             
              <tr v-for="app in selectedApps" :key="app.id">
              <td>{{lanId}}</td>
              <td>{{app.id}}</td>
              <td>{{app.name}}</td>
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
    deviceType:Object,
    device:"Base"
  },
  methods:{
    checkDeviceType(){
      this.device
      this.deviceType.map((type)=>{})
    }
  }
};
</script>
