<template>
  <v-app>
    <v-app-bar
      app
      color="blue lighten-1"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          :src="require('./assets/logo.svg')"
          transition="scale-transition"
          width="100"
        />
      </div>
    </v-app-bar>

    <v-main>
      <Multiplicacao @recarregar='recarregar' :key='this.chave'/>
    </v-main>
  </v-app>
</template>

<script>
import Multiplicacao from './components/Multiplicacao';

export default {
  name: 'App',

  components: {
    Multiplicacao
  },
  methods: {
    recarregar() {
      this.chave++;
    }
},
  data: () => ({
    chave: 0,
  }),
};
</script>
