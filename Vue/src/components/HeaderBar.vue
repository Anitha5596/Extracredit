<template>
  <header class="navbar">
    <div class="logo" @click="resetSection">My Portfolio</div>

    <div class="hamburger" @click="toggleMenu">
      <span class="line"></span>
      <span class="line"></span>
      <span class="line"></span>
    </div>

    <ul :class="['nav-links', { 'nav-active': menuOpen }]">
      <li>
        <a
          href="#about"
          :class="{ active: activeSection === 'about' }"
          @click="selectSection('about')"
        >About</a>
      </li>
      <li>
        <a
          href="#projects"
          :class="{ active: activeSection === 'projects' }"
          @click="selectSection('projects')"
        >Projects</a>
      </li>
      <li>
        <a
          href="#skills"
          :class="{ active: activeSection === 'skills' }"
          @click="selectSection('skills')"
        >Skills</a>
      </li>
      <li>
        <a
          href="#education"
          :class="{ active: activeSection === 'education' }"
          @click="selectSection('education')"
        >Education</a>
      </li>
      <li>
        <a
          href="#experience"
          :class="{ active: activeSection === 'experience' }"
          @click="selectSection('experience')"
        >Experience</a>
      </li>
      <li>
        <a
          href="#certifications"
          :class="{ active: activeSection === 'certifications' }"
          @click="selectSection('certifications')"
        >Certifications</a>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: 'HeaderBar',
  props: {
    activeSection: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      menuOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    selectSection(section) {
      this.menuOpen = false;
      this.$emit('section-selected', section);
    },
    resetSection() {
      this.menuOpen = false;
      this.$emit('section-selected', ''); 
      window.scrollTo({ top: 0, behavior: 'smooth' }); 
    }
  }
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #333;
  color: white;
  padding: 1em;
  position: relative;
}

.logo {
  font-size: 1.5em;
  font-weight: bold;
  cursor: pointer;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 1.5em;
}

.nav-links li a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s, border-bottom 0.3s;
  padding-bottom: 2px;
}

.nav-links li a.active {
  border-bottom: 2px solid #c44663;
  color: #c44663;
}

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
}

.hamburger .line {
  width: 25px;
  height: 3px;
  background-color: white;
}

@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav-links {
    position: absolute;
    top: 60px;
    right: 0;
    background-color: #444;
    width: 100%;
    flex-direction: column;
    align-items: center;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s ease-in-out;
  }

  .nav-links.nav-active {
    max-height: 400px;
  }

  .nav-links li {
    padding: 0.8em 0;
  }
}
</style>
