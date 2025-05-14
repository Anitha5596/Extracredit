<template>
  <section id="education" :class="['card', { active }]">
    <h2>Education</h2>
    <p>🏛️ Masters in CS- University of New Haven</p>
    <p>🏛️ Bachelors- Bharath University</p>
  </section>
</template>

<script>
export default {
  props: ['active']
}
</script>

<style scoped>
.card {
  background-color: #b37a8f;
  color: white;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  transition: background-color 0.3s ease;
}

.card.active {
  background-color: #918d8d;
}
</style>
