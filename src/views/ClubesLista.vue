<template>
  <div>
    <router-view />
    <v-container>
      <h2 class="text-h5 text-center mb-3 mt-5">Classificação dos Clubes</h2>
      <ClubesTabela :clubes="clubesOrdenados" />
    </v-container>
  </div>
</template>

<script>
import ClubesTabela from "../components/ClubesTabela";

export default {
  name: "ClubesLista",
  components: {
    ClubesTabela,
  },
  data() {
    return {
      clubesLista: [],
    };
  },

  computed: {
    clubesOrdenados() {
      const listaComputada = this.clubesLista.slice(0).sort(
        (a, b) =>  a.pontos > b.pontos ? -1 : 1
     );
    
      return listaComputada;
    }
  },

  created() {
    fetch("https://hackthon-decola.firebaseio.com/clubes-lista.json")
      .then((response) => response.json())
      .then((json) => {
        this.clubesLista = json;
      });
  },
};
</script>