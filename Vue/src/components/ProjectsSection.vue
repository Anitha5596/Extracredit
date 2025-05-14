<template>
  <section :class="['project-section', { active }]" id="projects">
    <h2>Projects</h2>
    <div class="project-grid">
      <div class="project-card">Portfolio Website with Vue</div>
      <div class="project-card">Real-Time Chat App</div>
      <div class="project-card">Task Tracker with MongoDB</div>
      <div class="project-card">Blog Platform (MEVN)</div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProjectSection',
  props: ['active'],
  data() {
    return {
      projects: []
    };
  },
  async created() {
    await this.fetchProjects();

    this.polling = setInterval(() => {
      this.fetchProjects();
    }, 5000);
  },
  beforeUnmount() {
    clearInterval(this.polling);
  },
  methods: {
    async fetchProjects() {
      try {
        const res = await fetch('http://localhost:5596/api');
        this.projects = await res.json();
        console.log('Updated projects:', this.projects);
      } catch (error) {
        console.error('Error fetching projects:', error);
      }
    }
  }
};
</script>




<style scoped>
.project-section {
  background-color: #b37a8f;
  border-radius: 10px;
  padding: 2em 1em;
  text-align: center;
  transition: background-color 0.3s ease;
}

.project-section.active {
  background-color: #918d8d;
}

.project-section h2 {
  color: white;
  margin-bottom: 1.8em;
  font-weight: bold;
  font-size: 1.8em;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
  padding: 0 1em;
}

.project-card {
  background-color: #855669;
  color: white;
  border-radius: 12px;
  padding: 1em;
  font-weight: bold;
  text-align: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transition: transform 0.2s ease, background-color 0.2s ease;
  cursor: pointer;
}

.project-card:hover {
  background-color: #333;
  transform: scale(1.03);
}
</style>
