<template>
  <main class="home">

    <!-- Cabeçalho da Home -->
    <section class="home-header">
      <h1>Bom dia!</h1>
      <p>Cuide da sua saúde, um horário de cada vez.</p>
    </section>

    <!-- Resumo do dia -->
    <section class="home-summary">

      <div class="summary-card">
        <p>Próximo horário</p>
        <h2>14:00</h2>
      </div>

      <div class="summary-card">
        <p>Tomados hoje</p>
        <h2>2</h2>
      </div>

      <div class="summary-card">
        <p>Pendentes</p>
        <h2>3</h2>
      </div>

    </section>

    <!-- Próximo medicamento -->
    <section class="next-medicine">

      <h2>Próximo medicamento</h2>

      <div class="medicine-card">

        <div class="medicine-info">
          <h3>Dipirona</h3>
          <p>1 comprimido</p>
        </div>

        <div class="medicine-time">
          <p>14:00</p>
          <span>Pendente</span>
        </div>

        <button type="button">
          Marcar como tomado
        </button>

      </div>

    </section>

  </main>
</template>

<script setup>
</script>

<style src="../assets/styles/home.css"></style>