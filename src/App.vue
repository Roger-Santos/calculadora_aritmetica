<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  primeiroValor: '',
  segundoValor: '',
  resultado: '',
  operador: 'adicao',
  historico: '',
})

function calcula() {
  switch (estado.operador) {
    case 'adicao':
      return parseInt(estado.primeiroValor) + parseInt(estado.segundoValor);
    case 'subtracao':
      return parseInt(estado.primeiroValor) - parseInt(estado.segundoValor);
    case 'multiplicacao':
      return parseInt(estado.primeiroValor) * parseInt(estado.segundoValor);
    default:
      return (parseInt(estado.primeiroValor) / parseInt(estado.segundoValor)).toFixed(2);
  }
}

function podeCalcular() {
  if (estado.primeiroValor != '' && estado.segundoValor != '') {
    return true;
  } else {
    return false;
  }
}

function setValores(evento) {
  switch (evento.target.id) {
    case 'input_valorA':
      estado.primeiroValor = evento.target.value;
      return;
    case 'input_valorB':
      estado.segundoValor = evento.target.value;
      return;
    default:
      estado.operador = evento.target.value;
      return;
  }
}

function main(evento) {
  console.log('Primeiro Valor:' + estado.primeiroValor);
  console.log('Segundo Valor:' + estado.segundoValor);
  console.log('Resultado Valor:' + estado.resultado);

  const contaAnterior = estado.operador + ' (' + estado.primeiroValor + ', ' + estado.segundoValor + ') = ' + estado.resultado;

  if (estado.resultado != '') {
    console.log("Já existe uma conta");
    estado.historico = contaAnterior;
  }

  setValores(evento);

  if (podeCalcular()) {
    estado.resultado = calcula();
  }
}



</script>

<template>

  <div class="container">
    <Cabecalho :historico="estado.historico" />
    <Formulario :insere-valor="evento => main(evento)" :resultado="estado.resultado" />

  </div>
</template>

<style scoped></style>
