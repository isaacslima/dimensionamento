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
                <v-autocomplete v-model="cnaeSelecionado" :items="listaCnaes" outlined chips color="blue-grey lighten-2"
                  label="Cnaes" item-text="codigos" return-object>
                  <template v-slot:selection="data">
                    <v-chip v-bind="data.attrs" :input-value="data.selected" @click="data.select">
                      <v-avatar left>
                        <v-img :src="data.item.avatar"></v-img>
                      </v-avatar>
                      {{ data.item.codigos }} - {{ data.item.denominacao }}    <b>Grau de Risco:</b> {{ data.item.gr }}
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

                <v-text-field
                  label="Número de funcionários"
                  outlined
                  v-model="numeroFuncionarios"
                  :disabled="!cnaeSelecionado"
                ></v-text-field>
                <v-btn block @click="atualizaEnquadramento">
                  Consultar
                </v-btn>
                <div v-if="atualizar">
                  <h1>Enquadramento Grau {{ cnaeSelecionado.gr }}</h1>
                  <h2>Téc de Seg Trabalho - {{ enquadramento.tecSegTrabalho  }}</h2>
                  <h2>Eng de Seg Trabalho - {{ enquadramento.engSegTrabalho }}</h2>
                  <h2>Aux. Enfermagem Trabalho - {{ enquadramento.auxEnfermagemTrabalho }}</h2>
                  <h2>Enfermeiro do Trabalho - {{ enquadramento.enfermeiroTrabalho }}</h2>
                  <h2>Médico do Trabalho - {{ enquadramento.medicoTrabalho }}</h2>
                </div>
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
import quadroDimensionamento from '../dictionary/quadroDimensionamento'

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
      numeroFuncionarios: 0,
      atualizar: false,
      enquadramento: {
        tecSegTrabalho: 0,
        engSegTrabalho: 0,
        auxEnfermagemTrabalho: 0,
        enfermeiroTrabalho: 0,
        medicoTrabalho: 0
      },
      listaQuadroDimensionamento: quadroDimensionamento,
      listaCnaes: cnaes,
      tab: 0,
      cnaeSelecionado: ''
    }),
    methods: {
      atualizaEnquadramento () {
        this.atualizar = true;
        var ar = this.listaQuadroDimensionamento[this.cnaeSelecionado.gr];
        if(this.numeroFuncionarios < 50 ){
          this.enquadramento = ar[50];
        } else if (this.numeroFuncionarios < 100 ){
          this.enquadramento = ar[100];
        }else if (this.numeroFuncionarios < 250 ){
          this.enquadramento = ar[250];
        } else if (this.numeroFuncionarios < 500 ){
          this.enquadramento = ar[500];
        } else if (this.numeroFuncionarios < 1000 ){
          this.enquadramento = ar[100];
        } else if (this.numeroFuncionarios < 2000 ){
          this.enquadramento = ar[2000];
        } else if (this.numeroFuncionarios < 3500 ){
          this.enquadramento = ar[3500];
        } else if (this.numeroFuncionarios < 5000 ){
          this.enquadramento = ar[5000];
        } else {
          this.enquadramento = ar[9999];
        }
        
      }
    }
  }
</script>
