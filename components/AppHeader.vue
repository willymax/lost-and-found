<!-- Header Section:

Logo: Your platform's distinctive logo
Navigation Menu: Links to key sections of the site (Home, How It Works, About Us, Contact)
Call-to-Action (CTA) Buttons: "Report Lost Document" and "Post Found Document"
Login/Sign Up: Links or buttons for user authentication -->
<template>
  <v-app-bar app color="primary" dark>
    <v-toolbar-title>
      <!-- <v-img src="/path/to/your/logo.png" alt="Logo" max-height="40" max-width="40" contain></v-img> -->
      <h1>Lost & Found</h1>
    </v-toolbar-title>

    <v-spacer></v-spacer>
  </v-app-bar>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>
<style scoped>
.app-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  background-color: #f8f9fa;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Add more styles as needed */
</style>
