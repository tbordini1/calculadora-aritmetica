<template>
  <div class="container py-5">
    <div class="row justify-content-center">
      <div class="col-md-6 col-lg-4">
        <div class="card shadow">
          <div class="card-header bg-primary text-white text-center">
            <h2>Calculadora Aritmética</h2>
          </div>
          <div class="card-body">
            <form>
              <div class="mb-3">
                <label for="num1" class="form-label">Número 1</label>
                <input
                  type="number"
                  id="num1"
                  class="form-control"
                  v-model.number="num1"
                  placeholder="Digite o primeiro número"
                />
              </div>
              <div class="mb-3">
                <label for="num2" class="form-label">Número 2</label>
                <input
                  type="number"
                  id="num2"
                  class="form-control"
                  v-model.number="num2"
                  placeholder="Digite o segundo número"
                />
              </div>
              <div class="mb-4">
                <label for="operacao" class="form-label">Operação</label>
                <select
                  id="operacao"
                  class="form-select"
                  v-model="operacao"
                >
                  <option value="soma">Adição (+)</option>
                  <option value="subtracao">Subtração (-)</option>
                  <option value="multiplicacao">Multiplicação (×)</option>
                  <option value="divisao">Divisão (÷)</option>
                </select>
              </div>
              <div class="alert alert-info text-center">
                <strong>Resultado:</strong> {{ resultado }}
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operacao: "soma",
    };
  },
  computed: {
    resultado() {
      switch (this.operacao) {
        case "soma":
          return this.num1 + this.num2;
        case "subtracao":
          return this.num1 - this.num2;
        case "multiplicacao":
          return this.num1 * this.num2;
        case "divisao":
          return this.num2 !== 0
            ? (this.num1 / this.num2).toFixed(2)
            : "Erro: divisão por zero!";
        default:
          return "Operação inválida";
      }
    },
  },
};
</script>

<style scoped>
.card {
  border-radius: 10px;
}
</style>
