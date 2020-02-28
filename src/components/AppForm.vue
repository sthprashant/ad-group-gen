<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-row>
            <v-text-field placeholder="LAN ID" dense outlined></v-text-field>
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
            clearable="clear"
            @change="sendSelectedApps"
          ></v-overflow-btn>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
  <!-- <div>
          <ul>
            <li>{{selectedApps}}</li>
          </ul>
  </div>-->
</template>

<script>
export default {
  name: "app-form",
  props: {
    apps: Array
  },
  methods: {
    sendSelectedApps() {
      this.$emit("send:apps", this.selectedApps);
    }
  },
  data() {
    return {
      selectedApps: []
    };
  }
};
</script>
