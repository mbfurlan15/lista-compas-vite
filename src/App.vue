<template>
  <h1>{{ titulo }}</h1>
  <input type="text" v-model="item.descricao" placeholder="Item de Compra" />
  <app-btn @click="addItem()">Adicionar</app-btn>
  <!-- Montando a tabela de lista de compras -->
  {{listaCompras}}
  <table border="1">
    <thead>
      <th>Carrinho</th>
      <th>Item</th>
      <th>Valor</th>
    </thead>
    <tr v-for="iterador in listaCompras" :key="iterador" :class="{ riscado: iterador.concluido }">
      <td>
        <input type="checkbox" v-model="iterador.concluido" />
      </td>
      <td>{{ iterador.descricao }}</td>
      <td>
        <input type="number" v-model="iterador.valor" placeholder="R$" :disabled="iterador.concluido"/>
      </td>
    </tr>
  </table>
  <app-btn @click="somarCompra()">Somar Compra</app-btn>
  <p>{{valorCompra}}</p>
</template>

<script setup>
import AppBtn from "./components/AppBtn.vue";
import { reactive, ref } from "vue";
const titulo = ref("Lista de Compras");
const Listas = reactive([]);
const listaCompras = reactive([]);
const item = reactive({
  concluido: false,
  descricao: "",
  valor: Number,
});
let valorCompra = 0

function addItem() {
  listaCompras.push(Object.assign({}, item));
}
function somarCompra(){
  for (let index = 0; index < this.listaCompras.length; index++) {
    valorCompra += this.listaCompras[index].valor;
    
  }
  return valorCompra
}

</script>

<style>
.riscado {
  text-decoration: line-through;
}
</style>
