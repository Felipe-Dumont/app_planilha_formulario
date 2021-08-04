<template>
  <v-row class="d-flex justify-center align-center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Bem-vindo ao sistema que transforma um arquivo excel em um CRUD
        </v-card-title>
        <v-card-text>
          <p>
            Para começar precisamos de um arquivo de excel, podendo ele conter
            informações ou não.
          </p>
          <p>
            Arraste o arquivo ou clique no campo a baixo para selecioanr o
            arquivo.
          </p>
          <hr class="my-3" />
        </v-card-text>
        <v-card-actions>
          <v-row align="center" no-gutters>
            <v-file-input
              v-if="!jaCarregado"
              v-model="arquivo"
              label="File input"
              outlined
              dense
              @change="uploadArquivo"
            ></v-file-input>
            <v-btn v-if="jaCarregado" block @click="jaCarregado = false"
              >Avançar</v-btn
            >
          </v-row>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      jaCarregado: false,
      arquivo: null,
    }
  },
  methods: {
    uploadArquivo() {
      // eslint-disable-next-line no-console
      console.log(this.arquivo)

      if (this.arquivo === null) {
        return false
      }

      this.$axios
        .$get('example')
        // eslint-disable-next-line no-console
        .then((response) => console.log(response))
        // eslint-disable-next-line no-console
        .catch((err) => console.log(err))

      this.jaCarregado = true
    },
  },
}
</script>
