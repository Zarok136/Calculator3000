<script setup>
import Calculator from './components/Calculator.vue'
</script>

<template>
<Calculator></Calculator>
<footer>©️ Benoit Nowak - 2024
<a href="https://github.com/Zarok136"><img src="./assets/img/github.svg" alt="githublogo"></a>
</footer>
</template>

<style scoped>
footer{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  margin-top: 20px;
}

img{
  width: 3rem;
  margin-left: 10px;
}
</style>
