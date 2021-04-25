<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12" class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">Digite o multiplicador e o multiplicando</h1>
      </v-col>

      <v-col cols="12">
        <v-card>
          <v-card-title>
            <v-row justify="center" class="ma-2">
              <div class="display-1 mr-5">Quanto é</div>
              <div class="entrada">
                <v-text-field
                  v-mask="'#'"
                  class="display-1 mt-0 pt-0"
                  v-model.number="multiplicador"
                ></v-text-field>
              </div>

              <p class="display-1 mr-5 ml-5">x</p>
              <div class="entrada">
                <v-text-field
                  v-mask="'#'"
                  class="display-1 mt-0 pt-0"
                  v-model.number="multiplicando"
                ></v-text-field>
              </div>
            </v-row>
          </v-card-title>
          <v-row justify="space-around" no-gutters v-if="calculo == true">
            <v-col cols="4" v-for="n in multiplicador" :key="n">
              <v-card width="33,3%" class="ma-5 pa-5 yellow accent-1">
                <v-card-title>{{n}}</v-card-title>
                <v-card-text class="ma-5 pa-5">
                  <v-row>
                    <v-col cols="4" v-for="y in multiplicando" :key="y">
                      <v-icon class="outlined green lighten-2">{{y}}</v-icon>
                    </v-col>
                  </v-row>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-card>
      </v-col>

      <v-col cols="12" v-if="calculo == true">
        <Alternativas @recarregar="recarregar" :resposta="resposta" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Alternativas from '../components/Respostas/Alternativas';
export default {
  name: "Multiplicação",
  components: {
    Alternativas,
  },
  data: () => ({
    multiplicador: null,
    multiplicando: null,
    contador: 2,
    resposta: 0,
    listaRespostas: [],
    opcoes: [],
    casas: 0
  }),
  methods: {
    calcularResposta() {
      this.resposta = this.multiplicador * this.multiplicando;
    },
    recarregar() {
       this.$emit('recarregar');
    }
  },
  computed: {
    calculo() {
      if (this.multiplicador !== null && this.multiplicando !== null) {
        this.calcularResposta();
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.v-icon.outlined {
  border: 1px solid currentColor;
  border-radius: 50%;
  height: 56px;
  width: 56px;
}

.entrada {
  width: 2vw;
}
</style>