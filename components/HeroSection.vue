<template>
  <v-sheet class="hero-section" elevation="3" rounded="lg" width="100%">
    <div class="text-center">
      <v-row>
        <v-col cols="12">
          <h1 class="text-h2 font-weight-bold mb-4">Find Your Lost Documents</h1>
          <p class="text-h5 mb-6">
            Search, report, and get notified when your documents are found.
          </p>
        </v-col>
      </v-row>
    </div>
    <div>
      <v-row class="d-flex justify-center">
        <v-col cols="8">
          <v-tabs
            v-model="tab"
            :items="tabs"
            align-tabs="center"
            color="deep-purple-accent-4"
            height="60"
            slider-color="#f78166"
            grow
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
                    <v-col cols="12" class="d-flex justify-center center">
                      <v-text-field
                        v-model="searchQuery"
                        label="Search"
                        prepend-icon="mdi-magnify"
                        variant="outlined"
                        class="mr-2"
                        @keyup.enter="searchDocument"
                        :disabled="searching"
                      ></v-text-field>
                      <v-btn
                        color="primary"
                        class="mx-2"
                        @click="searchDocument"
                        :disabled="searching"
                      >
                        <v-icon v-if="searching">mdi-loading</v-icon>
                        <span v-else>Search</span>
                      </v-btn>
                    </v-col>
                  </v-row>
                  <v-row v-if="searchResults.length > 0" class="mt-4">
                    <v-col cols="12">
                      <v-list>
                        <v-list-item v-for="result in searchResults" :key="result.id">
                          <template v-slot:prepend>
                            <v-avatar color="blue">
                              <v-icon color="white">mdi-clipboard-text</v-icon>
                            </v-avatar>
                          </template>
                          <template v-slot:append>
                            <v-btn
                              color="grey-lighten-1"
                              icon="mdi-information"
                              variant="text"
                            ></v-btn>
                          </template>
                          <v-list-item-content>
                            <p><strong>Document Name:</strong> {{ result.name }}</p>
                            <p>
                              <strong>Found At:</strong>
                              {{ result.location }}
                            </p>
                            <p><strong>Contact:</strong> {{ result.contactInfo }}</p>
                            <p><strong>Additional Info:</strong> {{ result.additionalInfo }}</p>
                            <v-chip
                              v-for="keyword in result.keywords"
                              :key="keyword"
                              class="ma-1"
                              color="primary"
                              label
                              >{{ keyword }}</v-chip
                            >
                          </v-list-item-content>
                        </v-list-item>
                      </v-list>
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
                        label="Name On The Document"
                        outlined
                        dense
                        class="mb-4"
                      ></v-text-field>
                      <v-text-field
                        v-model="lastLocation"
                        label="Location Lost/Found"
                        outlined
                        dense
                        class="mb-4"
                      ></v-text-field>
                      <!-- type of document -->
                      <v-select
                        v-model="documentType"
                        :items="documentTypes"
                        label="Document type"
                        outlined
                        dense
                        class="mb-4"
                      ></v-select>
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
        </v-col>
      </v-row>
    </div>
  </v-sheet>
</template>

<script>
export default {
  data() {
    return {
      tab: "search",
      searchQuery: "",
      tab: "tab-1",
      searching: false,
      searchResults: [],
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
      this.searching = true;
      console.log("Searching for document:", this.searchQuery);
      setTimeout(() => {
        this.searching = false;
        this.searchResults = [
          {
            id: 1,
            name: "Document 1",
            location: "Location 1",
            contactInfo: "Contact 1",
            additionalInfo: "Additional Info 1",
            keywords: ["Keyword 1", "Keyword 2"],
          },
          {
            name: "Document 1",
            location: "Location 1",
            date: "2021-01-01",
            status: "Lost",
            keywords: ["National Id", "University Id"],
            description: "Description 1",
            image: "image1.jpg",
            id: 1,
          },
        ];
      }, 1000);
    },
    setUpAlerts() {
      // Implement alert setup logic here
    },
  },
};
</script>

<style scoped>
.hero-section {
  background-color: #f5f5f5;
  padding: 64px 0;
}
</style>
