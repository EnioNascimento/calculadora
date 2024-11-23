<script setup>
import { reactive } from 'vue';
import '../node_modules/bootstrap/dist/css/bootstrap.min.css'


const estado = reactive({
  filtro: '',
  numero1: 0,
  numero2: 0,
  resultado: 0
})

function soma(){
  const { numero1, numero2 } = estado;
  return parseInt(numero1) + parseInt(numero2);
}

function diminuir(){
  const { numero1, numero2 } = estado;
  return (numero1 - numero2);
}

function multiplicar(){
  const { numero1, numero2 } = estado;
  return (numero1 * numero2);
}

function dividir(){
  const { numero1, numero2 } = estado;
  return parseInt(numero1) / parseInt(numero2);
}

const getOperacao = () =>{
  const { filtro } = estado;
  switch(filtro){
    case 'soma':
      return soma();
      case 'diminuir':
        return diminuir();
        case 'multiplicar':
          return multiplicar();
          case 'dividir':
            return dividir();
        default:
          return soma()
  }
}

</script>

<template>
<div class="container">
  <h1 class="display-5 fw-bold text-center pb-5">CALCULADORA BÁSICA</h1>
<form @select="getOperacao()" action="">
  <div class="row">
    <div class="col-md-3">
      <label for=""><h4>Primeiro número</h4></label>
  <input @keyup="evento => estado.numero1 = evento.target.value" type="text" class="form-control" placeholder="Digite o primeiro número..."> 
</div>
<div class="col-md-3 pb-5">
  <label for=""><h4>Segundo número</h4></label>
  <input @keyup="evento => estado.numero2 = evento.target.value" type="text" class="form-control" placeholder="Digite o segundo número...">
</div>
<div class="col-md-3 pb-5">
  <label for=""><h4>Selecione a Operação...</h4></label>
  <select @change="evento => estado.filtro = evento.target.value" name="" id="" class="form-control">
    <option value="soma">Somar</option>
    <option value="diminuir">Diminuir</option>
    <option value="multiplicar">Multiplicar</option>
    <option value="dividir">Dividir</option>
  </select>
</div>
</div>
<div class="col text-center">
  <label for=""><h4>Resultado</h4></label>
<h1>{{ getOperacao() }}</h1>
</div>
</form>
</div>
</template>

<style scoped>

</style>