<template>
  <div>
    <v-card>
      <v-card-title>Qual a resposta certa?</v-card-title>
      <v-row justify="center">
        <v-col cols="3" v-for="r in arrayRespostas" :key="arrayRespostas[r]">
          <v-btn color="success" @click="respostaClick(r)">{{r}}</v-btn>
        </v-col>
      </v-row>
    </v-card>

    <v-snackbar
      v-model="snackbar"
      :timeout="timeout"
      centered
      color="deep-purple accent-4"
      elevation="24"
    >{{ text }}</v-snackbar>
  </div>
</template>

<script>
export default {
  name: "Alternativas",
  props: ["resposta"],
  data: () => ({
    snackbar: false,
    text: "",
    timeout: 2000
  }),
  computed: {
    arrayRespostas() {
      var lista = [
        Math.floor(Math.random() * 82),
        Math.floor(Math.random() * 82),
        Math.floor(Math.random() * 82),
        Math.floor(Math.random() * 82)
      ];

      var respostaPos = Math.floor(Math.random() * 4);
      lista[respostaPos] = this.resposta;
      return lista;
    }
  },
  methods: {
    respostaClick(valor) {
      if (valor == this.resposta) {
        this.text = "Parabéns! Você acertou a resposta!";
        this.snackbar = true;
      } else {
        this.text = "Não foi desta vez. Tente novamente!",
        this.snackbar = true;
      }
      setTimeout(() => {  this.$emit('recarregar'); }, 2000);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>