<template>
  <div class="pagehome">
    <img src="@/assets/dubyicon.png" alt="Minha Imagem" />
    <CalculadorRenovacao />
    <RodapeCalcula />
  </div>
</template>

<script>
import CalculadorRenovacao from "./components/CalculadorRenovacao.vue";
import RodapeCalcula from "./components/rodapeCalcula.vue";

export default {
  components: {
    CalculadorRenovacao,
    RodapeCalcula,
  },
};
</script>

<style>
.pagehome{
  background-color: #322871;
}

</style>
