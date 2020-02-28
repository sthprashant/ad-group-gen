<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <v-form>
          <v-text-field placeholder="LAN ID"></v-text-field>
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
            @change="sendSelectedApps"
          ></v-overflow-btn>
        </v-form>

        <div>
          <ul>
            <li>
              {{selectedApps}}
            </li>
          </ul>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "app-form",
  props: {
    apps: Array,
  },
  methods: {
    sendSelectedApps() {
      this.$emit("send:apps", this.selectedApps);
    }
  },
  data() {
    return {
      selectedApps: [],
    }
  },
};
</script>
