<template>
  <v-app>
    <v-app-bar
      app
      white
    >
      <div class="d-flex align-center">
        <v-img
          alt="CIPA"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          max-width="auto"
          max-height="50"
          src="./assets/logo.jpg"
        />
        
      </div>

      <v-toolbar-title>Dimensionamento CIPA</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <Main/>
    </v-content>
  </v-app>
</template>

<script>
import Main from './components/Main';

export default {
  name: 'App',

  components: {
    Main,
  },

  data: () => ({
    //
  }),
};
</script>
