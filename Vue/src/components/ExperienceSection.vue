<template>
  <section id="experience" :class="['card', { active }]">
    <h2>Experience</h2>
    <p>🛠️ Software Intern - ABC Corp</p>
    <p>🛠️ Freelance Web Developer</p>
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
