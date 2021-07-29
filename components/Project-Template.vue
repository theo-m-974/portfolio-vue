<!-- eslint-disable vue/no-v-html -->
<template>
  <div id="modale" class="project-modale">
    <!-- <h3>{{ selectedProject.name }}</h3>
    <div class="close-btn" @click="displayModale()">X</div>

    <div class="project-info--grid">
      <div class="project-brief">
        <div class="project-brief-header">Chronologie</div>
        <div class="project-brief-content">
          {{ selectedProject.date }}
        </div>
      </div>
      <div class="project-brief">
        <div class="project-brief-header">Type</div>
        <div class="project-brief-content">
          {{ selectedProject.type }}
        </div>
      </div>
      <div class="project-brief">
        <div class="project-brief-header">Contribution</div>
        <div
          v-if="Object.keys(selectedProject).length != 0"
          class="project-brief-content"
        >
          <p v-for="contri in selectedProject.contribution" :key="contri">
            {{ contri }}
          </p>
        </div>
      </div>
      <div class="project-brief">
        <div class="project-brief-header">
          {{
            currentType == allProjects.prog ||
            currentType == allProjects.integration
              ? 'Langages'
              : 'Logiciels'
          }}
        </div>
        <div
          v-if="Object.keys(selectedProject).length != 0"
          class="project-brief-content"
        >
          <p v-for="langage in selectedProject.langages" :key="langage">
            {{ langage }}
          </p>
        </div>
      </div>
    </div>

    <div class="wrapper flex">
      <div class="project-wrapper">
        <div class="project-info-description">
          {{ selectedProject.description }}
        </div>
        <div v-if="selectedProject.link" class="btn-visit">
          <a :href="selectedProject.link" target="_blank">{{
            selectedProject.btnContent
          }}</a>
        </div>
      </div>

      <div
        v-if="Object.keys(selectedProject).length != 0"
        class="project-image-prez"
      >
        <img :src="selectedProject.imgs[0]" alt="" />
      </div>
    </div>

    <div
      v-if="selectedProject.iframe != undefined"
      class="project-video"
      v-html="selectedProject.iframe"
    ></div>

    <div
      v-if="Object.keys(selectedProject).length != 0"
      class="project-images--wrapper"
    >
      <div
        v-for="image in selectedProject.imgsNb"
        :key="image"
        class="project-image"
      >
        <img :src="selectedProject.imgs[image]" :alt="selectedProject.alt" />
      </div>
    </div> -->
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import $ from 'jquery'

export default {
  name: 'ProjectTemplate',

  // props: {},

  // data() {
  //   return {
  //     allProjects: projects,
  //     currentType: projects.prog,
  //     selectedProject: {},
  //     modaleIsDisplayed: false,
  //     isProjectMenuActive: false,
  //     isChecked: false,
  //   }
  // },

  // mounted() {
  //   this.$root.$on('selectProjectType', (e) => {
  //     if (e === 'prog') {
  //       this.modaleIsDisplayed = false
  //       return (this.currentType = this.allProjects.prog)
  //     } else if (e === 'integration') {
  //       this.modaleIsDisplayed = false
  //       return (this.currentType = this.allProjects.integration)
  //     } else if (e === 'design') {
  //       this.modaleIsDisplayed = false
  //       return (this.currentType = this.allProjects.design)
  //     } else if (e === 'audiovisuel') {
  //       this.modaleIsDisplayed = false
  //       return (this.currentType = this.allProjects.audiovisuel)
  //     }
  //   })
  // },

  // methods: {
  //   selectProject(e) {
  //     this.selectedProject = e
  //   },

  //   displayModale() {
  //     this.modaleIsDisplayed = !this.modaleIsDisplayed
  //   },

  //   displayProjectMenu() {
  //     this.isProjectMenuActive = !this.isProjectMenuActive
  //     this.isChecked = !this.isChecked
  //   },
  // },
}
</script>
