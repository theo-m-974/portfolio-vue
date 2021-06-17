<template>
  <div id="competences-anchor" class="competences section">
    <div class="wrapper--competences-prog">
      <h2>Programmation</h2>
      <div class="wrapper--icons">
        <div v-for="logoProg in progLogos" :key="logoProg" class="logo">
          <img :src="logoProg.src" :alt="logoProg.alt" />
        </div>
      </div>
    </div>
    <div class="wrapper--competences-design">
      <h2>Design</h2>
      <div class="wrapper--icons">
        <div v-for="logoDesign in designLogos" :key="logoDesign" class="logo">
          <img :src="logoDesign.src" :alt="logoDesign.alt" />
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
