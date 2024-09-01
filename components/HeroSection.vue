<template>
  <v-sheet color="#0d1117" elevation="3" rounded="lg">
    <v-tabs
      v-model="tab"
      :items="tabs"
      align-tabs="center"
      color="white"
      height="60"
      slider-color="#f78166"
    >
      <template v-slot:tab="{ item }">
        <v-tab
          :prepend-icon="item.icon"
          :text="item.text"
          :value="item.value"
          class="text-none"
        ></v-tab>
      </template>

      <template v-slot:item="{ item }">
        <v-tabs-window-item value="tab-1" class="pa-4">
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="searchQuery"
                  label="Search"
                  append-icon="mdi-magnify"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-tabs-window-item>
        <v-tabs-window-item value="tab-2" class="pa-4">
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="documentName"
                  label="Document name"
                  outlined
                  dense
                  class="mb-4"
                ></v-text-field>
                <v-text-field
                  v-model="lastLocation"
                  label="Last known location"
                  outlined
                  dense
                  class="mb-4"
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <v-btn color="warning" block>
                  <v-icon left>mdi-file-alert</v-icon>
                  Report Lost
                </v-btn>
              </v-col>
              <v-col>
                <v-btn color="success" block>
                  <v-icon left>mdi-file-check</v-icon>
                  Report Found
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-tabs-window-item>
        <v-tabs-window-item value="tab-3" class="pa-4">
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="email"
                  label="Enter your email"
                  outlined
                  dense
                  class="mb-4"
                ></v-text-field>
                <v-text-field
                  v-model="keywords"
                  label="Document keywords"
                  outlined
                  dense
                  class="mb-4"
                ></v-text-field>
                <v-btn color="info" block>
                  <v-icon left>mdi-bell</v-icon>
                  Set Up Alerts
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-tabs-window-item>
      </template>
    </v-tabs>
  </v-sheet>
</template>

<script>
export default {
  data() {
    return {
      tab: "search",
      searchQuery: "",
      tab: "tab-1",
      tabs: [
        {
          icon: "mdi-magnify",
          text: "Find Your Lost Document",
          value: "tab-1",
        },
        {
          icon: "mdi-hand-wave-outline",
          text: "Report a Found Document",
          value: "tab-2",
        },
        {
          icon: "mdi-bell-outline",
          text: "Get Notified",
          value: "tab-3",
        },
      ],
    };
  },
  methods: {
    searchDocument() {
      // Implement search logic here
    },
    setUpAlerts() {
      // Implement alert setup logic here
    },
  },
};
</script>

<style scoped>
.bg-gradient-to-r {
  background: linear-gradient(to right, #4299e1, #9f7aea);
}
</style>
