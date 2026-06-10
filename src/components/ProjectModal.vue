<template>
  <div class="modal fade" id="projectModal" tabindex="-1" ref="modalRef" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered modal-dialog-scrollable">
      <div class="modal-content" v-if="project">
        <div class="modal-header">
          <div>
            <h5 class="modal-title fw-bold">{{ project.titre }}</h5>
            <p v-if="project.date" class="text-muted small mb-0 mt-1">
              <i class="bi bi-calendar3 me-1"></i> {{ project.date }}
            </p>
          </div>
          <button type="button" class="btn-close" @click="closeModal"></button>
        </div>
        <div class="modal-body">
          <div class="mb-4" v-if="project.modalImage">
            <img :src="project.modalImage" class="img-fluid rounded w-100" :alt="project.titre">
          </div>
          
          <h5 class="fw-bold text-primary">Contexte</h5>
          <p class="text-slate-700" style="white-space: pre-line;">{{ project.contexte }}</p>
          
          <h5 class="fw-bold text-primary mt-4">Réalisation technique</h5>
          <p class="text-slate-700" style="white-space: pre-line;">{{ project.realisation }}</p>
          
          <ul v-if="project.pointsCles" class="mt-2">
            <li v-for="point in project.pointsCles" :key="point" class="mb-1">{{ point }}</li>
          </ul>

          <p v-if="project.realisation_2" class="text-slate-700 mt-3" style="white-space: pre-line;">
            {{ project.realisation_2 }}
          </p>
          
          <ul v-if="project.pointsCles_2" class="mt-2">
            <li v-for="point in project.pointsCles_2" :key="point" class="mb-1">{{ point }}</li>
          </ul>

          <p v-if="project.realisation_3" class="text-slate-700 mt-3" style="white-space: pre-line;">
            {{ project.realisation_3 }}
          </p>

          <h5 class="fw-bold text-primary mt-4" v-if="project.galerie">Galerie et Résultats</h5>
          <div class="row g-3" v-if="project.galerie">
            <div class="col-sm-6" v-for="img in project.galerie" :key="img.src">
              <img :src="img.src" class="img-fluid rounded" :alt="img.alt">
              <p class="text-muted small text-center mt-2">{{ img.alt }}</p>
            </div>
          </div>
          
          <h5 class="fw-bold text-success mt-4" v-if="project.resultatFinal">Résultats</h5>
          <p class="mt-1" v-if="project.resultatFinal">{{ project.resultatFinal }}</p>
        </div>
        <div class="modal-footer">
          <a :href="project.github" target="_blank" class="btn btn-outline-dark">
            <i class="bi bi-github"></i> Voir le code sur GitHub
          </a>
          <button type="button" class="btn btn-secondary" @click="closeModal">Fermer</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'

const props = defineProps({
  project: Object
})

const emit = defineEmits(['close'])
const modalRef = ref(null)
let modalInstance = null

onMounted(() => {
  if (window.bootstrap) {
    modalInstance = new window.bootstrap.Modal(modalRef.value)
  } else {
    import('bootstrap').then((bs) => {
      modalInstance = new bs.Modal(modalRef.value)
    })
  }
  modalRef.value.addEventListener('hidden.bs.modal', () => {
    emit('close')
  })
})

watch(() => props.project, (newProject) => {
  if (modalInstance) {
    if (newProject) {
      modalInstance.show()
    } else {
      modalInstance.hide()
    }
  }
})

const closeModal = () => {
  emit('close')
}
</script>