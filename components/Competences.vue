<template>
  <div id="competences" class="competences section">
    <div class="competences--section">
      <h2>Compétences</h2>
      <div class="competences--wrapper">
        <div class="wrapper--competences-prog">
          <h2>Programmation</h2>
          <div class="wrapper--icons">
            <div
              v-for="(logoProg, index) in progLogos"
              :key="index"
              class="logo"
            >
              <img :src="logoProg.src" :alt="logoProg.alt" />
            </div>
          </div>
        </div>
        <div class="wrapper--competences-design">
          <h2>Design</h2>
          <div class="wrapper--icons">
            <div
              v-for="(logoDesign, index) in designLogos"
              :key="index"
              class="logo"
            >
              <img :src="logoDesign.src" :alt="logoDesign.alt" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import competences from '@/assets/data/competences.js'

export default {
  name: 'Competences',

  data() {
    return {
      competencesLogos: competences,
      progLogos: competences.prog,
      designLogos: competences.design,
    }
  },
}
</script>
