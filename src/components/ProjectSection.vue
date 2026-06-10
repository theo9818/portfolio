<template>
  <section :id="id" class="py-5 bg-light">
    <div class="container">
      <h2 class="text-center fw-bold mb-5">{{ title }}</h2>
      <div class="row g-4">
        <div v-for="project in projects" :key="project.id" class="col-md-6 col-lg-4">
          <div class="card h-100 project-card">
            <div class="card-body">
              <div v-if="project.icon" class="text-primary mb-2">
                <i :class="['bi', project.icon, 'fs-3']"></i>
              </div>
              <img v-if="project.image && !project.icon" :src="project.image" class="img-fluid rounded mb-2" :alt="project.titre">
              
              <h5 class="card-title fw-bold mb-1">{{ project.titre }}</h5>
              
              <p v-if="project.date" class="text-primary small fw-semibold mb-2">
                <i class="bi bi-calendar3 me-1"></i> {{ project.date }}
              </p>
              
              <p class="card-text text-muted">{{ project.descriptionShort }}</p>
              <span v-for="tech in project.technos" :key="tech" class="badge bg-secondary me-1">{{ tech }}</span>
            </div>
            <div class="card-footer bg-white border-0 pb-3">
              <button type="button" class="btn btn-sm btn-outline-primary" @click="$emit('select-project', project)">
                Détails
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  id: String,
  title: String,
  projects: Array
})
defineEmits(['select-project'])
</script>

<style scoped>
.project-card {
  transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
}
.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.15);
}
</style>