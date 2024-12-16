<template>
  <div class="home-page">
    <h2>Renova BI</h2>
    <form @submit.prevent="calcularRenovacao">
      <div class="form-group">
        <label for="dias-restantes">Dias Restantes:</label>
        <input type="number" id="dias-restantes" v-model="diasRestantes" required />
      </div>

      <div class="form-group">
        <label for="data-atual">Data de Hoje:</label>
        <input type="date" id="data-atual" v-model="dataAtual" required />
      </div>

      <button type="submit">Calcular Data de Renovação</button>
    </form>

    <div v-if="dataRenovacao" class="result">
      <h3>Data de Renovação:</h3>
      <p>{{ dataRenovacao }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      diasRestantes: null,
      dataAtual: null,
      dataRenovacao: null,
    };
  },
  methods: {
    calcularRenovacao() {
      if (this.diasRestantes && this.dataAtual) {
        const diasParaRenovacao = this.diasRestantes - 15;
        if (diasParaRenovacao < 0) {
          alert("Já é hora de renovar sua assinatura! 🚀");
          return;
        }

        const dataBase = new Date(this.dataAtual);
        const dataRenovacao = new Date(
          dataBase.getTime() + diasParaRenovacao * 24 * 60 * 60 * 1000
        );

        this.dataRenovacao = dataRenovacao.toISOString().split("T")[0];
      } else {
        alert("Por favor, preencha todos os campos corretamente.");
      }
    },
  },
};
</script>

<style scoped>
@import url(https://fonts.googleapis.com/css?family=Nunito:200,300,regular,500,600,700,800,900,200italic,300italic,italic,500italic,600italic,700italic,800italic,900italic);

.home-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #412884, #322871);
  color: #fff;
  min-height: 60vh;
  padding: 20px;
  text-align: center;
  font-family: Nunito, Arial, Helvetica, sans-serif;
}

/* Cabeçalho */
h2 {
  font-size: 2rem;
  margin-bottom: 20px;
}

/* Formulário */
form {
  display: flex;
  flex-direction: column;
  background: #262756;
  backdrop-filter: blur(10px);
  padding: 20px;
  border-radius: 12px;
  width: 100%;
  max-width: 400px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.form-group {
  margin-bottom: 15px;
}

label {
  font-size: 1rem;
  margin-bottom: 5px;
  text-align: left;
  display: block;
}

input {
  padding: 10px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  width: 100%;
  box-sizing: border-box;
}

input:focus {
  outline: none;
  border-color: #6a11cb;
  box-shadow: 0 0 5px rgba(106, 17, 203, 0.5);
}

/* Botão */
button {
  padding: 10px 20px;
  font-size: 1rem;
  background: #73ba60;
  color: #fff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease;
}

button:hover {
  background: #12283f;
}

/* Resultado */
.result {
  margin-top: 20px;
  background: rgba(255, 255, 255, 0.1);
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.result h3 {
  margin-bottom: 10px;
}

.result p {
  font-size: 1.2rem;
  font-weight: bold;
  color: #f6f6f6;
}
</style>
