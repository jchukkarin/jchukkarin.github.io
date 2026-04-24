<script setup>
import AboutSection from '@/components/AboutSection.vue'
import TestimonialsSection from '@/components/WorkSection.vue'
import ContactSection from '@/components/ContactSection.vue'
import SkillsSection from '@/components/SkillsSection.vue'
import ExperienceSection from '@/components/ExperienceSection.vue'
import WorkSection from '@/components/WorkSection.vue'
</script>

<template>
  <section id="home" class="hero">
    <div class="container hero-wrapper">
      <!-- LEFT -->
      <div class="hero-text">
        <h1>Hi, I'm <span>Chukkarin</span></h1>

        <p class="p">
          A 4th-year Software Engineering student from the University of Phayao, currently interning
          and developing skills as a DevOps Engineer. I am learning and developing skills related to
          Docker, Kubernetes, CI/CD, and Cloud Infrastructure. I have a background in web
          development and backend systems, including an understanding of system deployment processes
          and basic infrastructure management. I am currently seeking an internship opportunity from
          May to September to further develop practical skills and gain valuable experience in
          DevOps.
        </p>
      </div>

      <!-- RIGHT -->
      <div class="hero-image">
        <div class="image-wrapper">
          <img src="/ME03.png" alt="profile" />
        </div>
      </div>
    </div>
  </section>

  <!-- แยก component -->
  <AboutSection />
  <SkillsSection />
  <ExperienceSection />
  <WorkSection />
  <ContactSection />
</template>

<style scoped>
.container {
  width: 100%;
  max-width: 1100px;
  margin: 0 auto;
  padding: 100px 20px 50px;
}

.hero-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  text-align: left;
}

/* LEFT */
.hero-text {
  flex: 1;
}

.hero-text h1 {
  margin-bottom: 16px;
}

.hero-text .p {
  margin-bottom: 24px;
}

/* RIGHT */
.hero-image {
  flex: 1;
  display: flex;
  justify-content: center;
}

.image-wrapper {
  position: relative;
}

.image-wrapper img {
  width: 300px;
  border-radius: 20px;
  object-fit: cover;
  position: relative;
  z-index: 2;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
  transition: 0.3s;
  transform: rotateY(-5deg) rotateX(5deg);
}

.image-wrapper img:hover {
  transform: rotateY(0deg) rotateX(0deg) scale(1.05);
}

/* background effect */
.image-wrapper::before {
  content: '';
  position: absolute;
  top: 20px;
  left: -20px;
  width: 100%;
  height: 100%;
  background: #e5e7eb;
  z-index: 1;
  border-radius: 20px;
  transform: rotateY(-5deg) rotateX(5deg) translateZ(-10px);
}

/* responsive */
@media (max-width: 768px) {
  .hero-wrapper {
    flex-direction: column;
    text-align: center;
  }

  .hero h1 {
    text-align: center;
  }

  .image-wrapper img {
    width: 200px;
  }

  .image-wrapper::before {
    display: none; /* ซ่อน background effect บนมือถือ */
  }
}

.hero {
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 60px;
}
.p {
  margin-top: 20px;
  font-size: 18px;
  line-height: 1.8;
  color: var(--subtext);
  max-width: 600px;
}

.hero h1 {
  font-size: 56px;
  font-weight: 700;
  line-height: 1.2;
  letter-spacing: -1px;
  text-align: left;
}

.hero span {
  color: #6366f1;
}
</style>
