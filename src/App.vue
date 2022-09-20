<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>

<template>
  <h1>Buscar CEP</h1>
  <form @submit.prevent="buscar" class="formulario1">
    <label>CEP</label>
    <input type="text" v-model="cep" />
    <button type="submit">Buscar</button>
  </form>
  <form class="formulario2">
    <label for="rua">Rua</label>
    <input name="rua" type="text" v-model="endereco.logradouro" />
    <label for="numero">Numero</label>
    <input name="numero" type="text" v-model="endereco.numero" />
    <label for="complemento">Complemento</label>
    <input name="complemento" type="text" v-model="endereco.complemento" />
    <label for="bairro">Bairro</label>
    <input name="bairro" type="text" v-model="endereco.bairro" />
    <label for="localidade">Cidade</label>
    <input name="cidade" type="text" v-model="endereco.localidade" />
    <label for="uf">Estado</label>
    <input name="estado" type="text" v-model="endereco.uf" />
  </form>
</template>

<style scoped>
.formulario1 {
  width: 200px;
  height: 80px;
  background-color: rgb(244, 244, 244);
  border: 1px solid lightgrey;
}
.formulario2 {
  width: 200px;
  height: 230px;
  background-color: rgb(244, 244, 244);
  border: 1px solid lightgray;
}
input {
  border: 1px solid rgb(163, 163, 163);
  align-self: center;
}
button {
  border: 1px solid rgb(163, 163, 163);
  background-color: white;
  width: 60px;
  height: 30px;
  margin: 10px 65px;
}
</style>
