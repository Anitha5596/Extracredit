<template>
  <section id="certifications" :class="['card', { active }]">
    <h2>Certifications</h2>
    <p>🏅 Python Programming</p>
    <p>🏅 Corporate Grooming & Communication</p>
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
