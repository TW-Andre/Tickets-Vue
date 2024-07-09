<script setup>

import {ref} from "vue";

let qty = ref();
let ticketType = ref('inferior');
let qtyTrack = ref(100);
let qtySuperior = ref(200);
let qtyInferior = ref(400);

  function buyTicket(event) {

    if (!qty.value) return alert("Você Precisa Digitar a Quantidade!");

    switch (ticketType.value) {
      case "pista":
        if (qtyTrack.value < qty.value) {
          alert('Não Há Ingressos Suficientes!')
        } else {
          qtyTrack.value -= parseInt(qty.value);
          alert(`Compra de ${qty.value} Ingressos Realizada com Sucesso!`)
        }
        break;
      case "superior":
        if (qtySuperior.value < qty.value) {
          alert(`Não há Ingressos Suficientes!`)
        } else {
          qtySuperior.value -= parseInt(qty.value);
          alert(`Compra de ${qty.value} Ingressos Realizada com Sucesso!`)
        }
        break;
      case "inferior":
        if (qtyInferior.value < qty.value) {
          alert(`Não há Ingressos Suficientes!`)
        } else {
          qtyInferior.value -= parseInt(qty.value);
          alert(`Compra de ${qty.value} Ingressos Realizada com Sucesso!`)
        }
        break;
    }
    qty.value = '';
  }
</script>

<template>
  <div class="d-flex">
    <header>
      <img class="logo" src="./assets/PNG/Logo e-tricket.png" alt="Logo">
    </header>
    <main class="container">

      <div class="grafismo"></div>
      <h1>Compre seu <span>ingresso</span></h1>
      <form action="">
        <label class="input-group">
          Escolha o tipo
          <select name="tipo-ingresso" id="tipo-ingresso" v-model="ticketType">
            <option value="inferior">Cadeira inferior</option>
            <option value="superior">Cadeira superior</option>
            <option value="pista">Pista</option>
          </select>
        </label>
        <label class="input-group">Qtde.
          <input type="number" v-model="qty" id="qtd" placeholder="00">
        </label>
        <button @click="buyTicket" type="button">Comprar</button>
      </form>
      <div class="hachuras"></div>
      <section>
        <h2>Quantidade disponível</h2>

        <ul class="lista">
          <li>Pista<span id="qtd-pista">{{ qtyTrack }}</span></li>
          <li>Cadeira superior<span id="qtd-superior">{{ qtySuperior }}</span></li>
          <li>Cadeira inferior<span id="qtd-inferior">{{ qtyInferior }}</span></li>

        </ul>
        <img src="./assets/Ingresso.svg" alt="" width="200px">
      </section>
    </main>
  </div>
</template>

<style scoped>

</style>
