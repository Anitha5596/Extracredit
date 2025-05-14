<template>
  <div :class="['app', theme]" id="app">
    <div id="portfolio-content">
      <HeaderBar
        :active-section="activeSection"
        @section-selected="handleSectionChange"
      />

      <main class="grid">
        <AboutSection :active="activeSection === 'about'" :about="portfolio.about" />
        <ProjectsSection :active="activeSection === 'projects'" :projects="portfolio.projects" />
        <SkillsSection :active="activeSection === 'skills'" :skills="portfolio.skills" />
        <EducationSection :active="activeSection === 'education'" :education="portfolio.education" />
        <ExperienceSection :active="activeSection === 'experience'" :experience="portfolio.experience" />
        <CertificationsSection :active="activeSection === 'certifications'" :certifications="portfolio.certifications" />
      </main>

      <FooterBar />
    </div>

    <div class="button-group">
      <button @click="exportToPDF" class="export-btn">📄 Export Portfolio as PDF</button>
      <button @click="toggleTheme" class="theme-btn">
        {{ theme === 'light' ? '🌙 Dark Mode' : '☀️ Light Mode' }}
      </button>
    </div>
  </div>
</template>

<script>
import HeaderBar from './components/HeaderBar.vue';
import FooterBar from './components/FooterBar.vue';
import AboutSection from './components/AboutSection.vue';
import ProjectsSection from './components/ProjectsSection.vue';
import SkillsSection from './components/SkillsSection.vue';
import EducationSection from './components/EducationSection.vue';
import ExperienceSection from './components/ExperienceSection.vue';
import CertificationsSection from './components/CertificationsSection.vue';
import html2pdf from 'html2pdf.js';

export default {
  data() {
    return {
      activeSection: '', 
      theme: 'light',
      portfolio: {
        about: [],
        skills: [],
        projects: [],
        education: [],
        certifications: [],
        experience: [],
        contact: {
          email: '',
          phone: ''
        }
      }
    };
  },
  components: {
    HeaderBar,
    FooterBar,
    AboutSection,
    ProjectsSection,
    SkillsSection,
    EducationSection,
    ExperienceSection,
    CertificationsSection
  },
  methods: {
    async fetchPortfolio() {
      try {
        const response = await fetch('https://portfolio-backend-zbe7.onrender.com/api');
        const data = await response.json();
        this.portfolio = data;
      } catch (error) {
        console.error('Failed to fetch portfolio:', error);
      }
    },
    exportToPDF() {
      const sourceEl = document.getElementById('portfolio-content');
      const clone = sourceEl.cloneNode(true);
      clone.className = sourceEl.className;

      const wrapper = document.createElement('div');
      wrapper.style.position = 'fixed';
      wrapper.style.top = '-9999px';
      wrapper.appendChild(clone);
      document.body.appendChild(wrapper);

      setTimeout(() => {
        html2pdf()
          .set({
            margin: 0.5,
            filename: 'my-portfolio.pdf',
            image: { type: 'jpeg', quality: 0.98 },
            html2canvas: { scale: 2 },
            jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' }
          })
          .from(clone)
          .save()
          .then(() => {
            document.body.removeChild(wrapper);
          });
      }, 200);
    },
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
    },
    handleSectionChange(section) {
      this.activeSection = section;
    }
  },
  async created() {
    await this.fetchPortfolio();
  }
};
</script>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
}

.app.light {
  background-color: #f0f8ff;
  color: #000;
}

.app.dark {
  background-color: #121212;
  color: #fff;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  padding: 1rem;
}

.button-group {
  text-align: center;
  margin-top: 1rem;
}

.export-btn,
.theme-btn {
  margin: 0.5rem;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
}

.export-btn {
  background-color: #c44663;
  color: white;
}

.theme-btn {
  background-color: #333;
  color: #fff;
}

.app.dark .export-btn {
  background-color: #c44663;
}

.app.dark .theme-btn {
  background-color: #d2cdce;
  color: #060606;
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
</style>
