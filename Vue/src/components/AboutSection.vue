<template>
  <section id="about" :class="['card', { active }]">
    <img src="https://img.icons8.com/?size=100&id=PB5JB8cGgxh1&format=png&color=000000" class="avatar" />
    <h1>ANITHA KONA</h1>
    <h2>About</h2>
    <p>Motivated and adaptable professional passionate about innovation and problem-solving.</p>
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

.avatar {
  width: 120px;
  border-radius: 50%;
  margin-bottom: 0.5rem;
}
</style>
