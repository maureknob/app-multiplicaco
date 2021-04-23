<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">Exercício de multiplicação</v-col>
      <v-col cols="12" class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">Digite o multiplicador e o multiplicando</h1>
      </v-col>

      <v-row justify="center">
        <v-col cols="4">
          <v-row align="center">
            <p class="display-1 mr-5 mb-0">Quanto é </p>
            <v-text-field class="display-1" v-model.number="multiplicador"></v-text-field>
          </v-row>
        </v-col>

        <v-col cols="4">
          <v-row align="center">
            <p class="display-1 mr-5 ml-5 mb-0"> x </p>
            <v-text-field class="display-1" v-model.number="multiplicando"></v-text-field>
          </v-row>
        </v-col>

        <v-col cols="12">
          <v-card v-if="calculo == true">
            <v-card-title>Quanto é {{multiplicador}} x {{this.multiplicando}} ?</v-card-title>
            <v-row no-gutters>
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
      </v-row>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Multiplicação",

  data: () => ({
    multiplicador: null,
    multiplicando: null,
    contador: 2
  }),
  computed: {
    calculo() {
      if (this.multiplicador !== null && this.multiplicando !== null) {
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
</style>