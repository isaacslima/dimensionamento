<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="col-md-3 col-xs-12">
        <v-img
          src="../assets/logo.jpg"
          class="my-3"
          contain
          height="100"
        />
      </v-col>
      <v-col class="mb-4">
        <v-card>
          <v-toolbar
            color="cyan"
            dark
            flat
          >
            <v-toolbar-title>Dimensionamento</v-toolbar-title>

            <template v-slot:extension>
              <v-tabs
                v-model="tab"
                align-with-title
              >
                <v-tabs-slider color="yellow"></v-tabs-slider>

                <v-tab >
                  NR 4
                </v-tab>
                <v-tab >
                  NR 5
                </v-tab>
              </v-tabs>
            </template>
          </v-toolbar>

          <v-tabs-items v-model="tab">
            <v-tab-item>
              <v-card flat>
                <v-card-text>Quadro Dimensionamento SESMT ANEXO I</v-card-text>
              </v-card>
            </v-tab-item>
            <v-tab-item>
              <v-card flat>
                <v-card-text></v-card-text>
              </v-card>
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </v-col>


    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
    }),
  }
</script>
