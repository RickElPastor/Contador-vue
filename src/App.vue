<script setup>
  import { ref, onMounted, watch } from 'vue'
  const count = ref(0)
  const minCount = ref(0)


  const increment = () => {
    count.value++
  }

  const decrement = () => {
    if (count.value > minCount.value) {
      count.value--
    }
  }

  const reset = () => {
    count.value = 0
  }

  onMounted(() => {
    if (localStorage.getItem('count')) {
      count.value = parseInt(localStorage.getItem('count'))
    }
  })

  watch(count, (value) => {
    localStorage.setItem('count', value)
  })
</script>

<template>
  <div class="container">
    <h1>Contador Incremental</h1>
    <p>{{ count }}</p>
    <button @click="increment" class="up">Incrementar</button>
    <button @click="decrement" class="down">Decrementar</button>
    <button @click="reset" class="reset">Resetear</button>
  </div>
</template>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
  }
  p {
    font-size: 2rem;
    margin-bottom: 1rem;
  }
  button {
    font-size: 1.5rem;
    padding: 0.5rem 1rem;
    margin-bottom: 1rem;
  }
  .up {
    background-color: #4c82af;
    color: white;
    border: none;
    border-radius: 5px;
  }
  .down {
    background-color: #f44336;
    color: white;
    border: none;
    border-radius: 5px;
  }
  .reset {
    background-color: #4caf50;
    color: white;
    border: none;
    border-radius: 5px;
  }
</style>
