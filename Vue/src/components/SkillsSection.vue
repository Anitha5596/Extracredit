<template>
  <section id="skills" :class="['card', { active }]">
    <h2>Skills</h2>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
      Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </p>
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
