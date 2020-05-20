<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <v-card>
          <v-toolbar
            color="cyan"
            dark
            flat
          >
            <v-toolbar-title centered>Dimensionamento</v-toolbar-title>

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
                <v-autocomplete
                    v-model="cnaeSelecionado"
                    :items="listaCnaes"
                    filled
                    chips
                    color="blue-grey lighten-2"
                    label="Cnaes"
                    item-text="codigos"
                    item-value="codigos"
                >
                  <template v-slot:selection="data">
                    <v-chip
                      v-bind="data.attrs"
                      :input-value="data.selected"
                      close
                      @click="data.select"
                      @click:close="remove(data.item)"
                    >
                      <v-avatar left>
                        <v-img :src="data.item.avatar"></v-img>
                      </v-avatar>
                      {{ data.item.codigos }}
                    </v-chip>
                  </template>
                  <template v-slot:item="data">
                    <template v-if="typeof data.item !== 'object'">
                      <v-list-item-content v-text="data.item"></v-list-item-content>
                    </template>
                    <template v-else>
                      <v-list-item-avatar>
                        <img :src="data.item.gr">
                      </v-list-item-avatar>
                      <v-list-item-content>
                        <v-list-item-title v-html="data.item.codigos"></v-list-item-title>
                        <v-list-item-subtitle v-html="data.item.denominacao"></v-list-item-subtitle>
                      </v-list-item-content>
                    </template>
                  </template>
                </v-autocomplete>

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
import cnaes from '../dictionary/cnaes'

  export default {
    name: 'Main',

    data: () => ({
      srcs: {
        1: '../assets/1.jpg',
        2: '../assets/1.jpg',
        3: '../assets/1.jpg',
        4: '../assets/1.jpg',
        5: '../assets/1.jpg',
      },
      listaCnaes: cnaes,
      tab: 0,
      cnaeSelecionado: ''
    }),
    methods: {
    remove (item) {
      const index = this.friends.indexOf(item.name)
      if (index >= 0) this.friends.splice(index, 1)
    },
  },
  }
</script>
