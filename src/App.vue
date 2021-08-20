<template>
<input type="text" v-model="itemCompra">
<button> Adicionar </button>
<p>{{itemCompra}}</p>
</template>

<script>
export default{
  data: () =>({
    itemCompra:"",
    itensCompras: {}
  })
}
</script>

<style>

</style>
