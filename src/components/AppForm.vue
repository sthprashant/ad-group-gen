<template>
  <v-row justify="center" align="center">
    <v-col cols="12" lg="4" md="6" sm="8">
      <v-row justify="center">
        <v-col cols="12" lg="3" md="5" sm="7" xs="2">
          <v-text-field placeholder="LAN ID" outlined dense v-model="lanId" @input="sendLanId"></v-text-field>
        </v-col>
      </v-row>
      <v-overflow-btn
        v-model="selectedApps"
        :items="apps"
        item-text="name"
        item-value="id"
        label="Select Apps"
        multiple
        editable
        dense
        @change="sendSelectedApps"
        rounded
        height-details="300px"
      >
        <template v-slot:selection="{ item, index }">
          <v-chip v-if="index === 0">
            <span>{{ item.name }}</span>
          </v-chip>
          <span
            v-if="index === 1"
            class="grey--text caption"
          >(+{{ selectedApps.length - 1 }} others)</span>
        </template>
      </v-overflow-btn>

      <v-row justify="center">
        <v-col class="text-center" cols="12" sm="3">
          <v-checkbox v-model="itSupport" label="IT Support" @change="sendCheckBoxStatus"></v-checkbox>
        </v-col>
      </v-row>

      <v-row justify="center">
        <v-col class="text-center" cols="12" sm="4">
          <div class="my-2">
            <v-btn @click="clearData" color="primary">Clear Data</v-btn>
          </div>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "app-form",
  props: {
    apps: Array
  },
  methods: {
    sendSelectedApps() {
      if (this.lanId !== "") this.$emit("send:apps", this.selectedApps);
    },
    sendLanId() {
      this.$emit("send:lanId", this.lanId);
      this.$emit("send:apps", this.selectedApps);
    },
    sendCheckBoxStatus() {
      this.$emit("send:itSupport", this.itSupport);
    },
    clearData() {
      this.lanId = "";
      this.selectedApps = [];
      this.sendSelectedApps();
      this.sendLanId();
    }
  },
  data() {
    return {
      selectedApps: [],
      lanId: "",
      itSupport: false
    };
  }
};
</script>
