<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <h1>AD Group Generator for AVC 2</h1>
      </v-col>
      <v-col>
        <v-form>
          <v-overflow-btn
            v-model="selectedApps"
            :items="apps"
            item-text="name"
            item-value="id"
            label="Select Apps"
            deletable-chips
            small-chips
            dense
            multiple
            editable
          ></v-overflow-btn>
        </v-form>
        <v-list>
            <v-list-item v-for="(selectedApp,i) in selectedApps" :key="i">
                <v-list-item-content>
                <v-list-item-title v-text="selectedApp" class="text-left"></v-list-item-title>
            </v-list-item-content>
            </v-list-item>
        </v-list>
        <!-- <ul class="text-left">
          <li v-for="(selectedApp,i) in selectedApps" :key="i">{{selectedApps[i]}}</li>
        </ul> -->
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "entry-form",
  props: {
    apps: Array
  },
  data() {
    return {
      selectedApps: []
    };
  }
  //   computed:{
  //       singleApp:function(){
  //           return this.apps.map((app) =>)
  //       }
  //   }
};
</script>