<!-- eslint-disable vue/no-v-html -->
<template>
  <div id="projects" class="projects section">
    <div class="projects-template">
      <div class="projects-title"><h2>Réalisations</h2></div>
      <div class="projects-nav">
        <ul>
          <li @click="selectProjectType('prog')"><h3>Programmation</h3></li>
          <li @click="selectProjectType('integration')">
            <h3>Intégration</h3>
          </li>
          <li @click="selectProjectType('design')"><h3>Design</h3></li>
          <li @click="selectProjectType('audiovisuel')">
            <h3>Audiovisuel</h3>
          </li>
        </ul>
      </div>
      <div class="projects-template--wrapper">
        <div
          v-for="(project, index) in currentType.length"
          :key="project.name"
          class="project-image"
          @click="
            selectProject(currentType[index])
            displayModale()
          "
        >
          <img
            :src="currentType[index].imgs[0]"
            :alt="currentType[index].alt"
          />
          <div class="project-name">
            {{ currentType[index].name }}
          </div>
        </div>
      </div>
      <div
        id="modale"
        class="project-modale"
        :class="modaleIsDisplayed ? 'displayed' : ''"
      >
        <h3>{{ selectedProject.name }}</h3>
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
            <img
              :src="selectedProject.imgs[image]"
              :alt="selectedProject.alt"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import projects from '@/assets/data/projects.js'
// eslint-disable-next-line no-unused-vars
import $ from 'jquery'

export default {
  name: 'Projects',

  props: {},

  data() {
    return {
      allProjects: projects,
      currentType: projects.prog,
      selectedProject: {},
      modaleIsDisplayed: false,
      isProjectMenuActive: false,
      isChecked: false,
    }
  },

  methods: {
    selectProject(e) {
      this.selectedProject = e
    },

    displayModale() {
      this.modaleIsDisplayed = !this.modaleIsDisplayed
    },

    displayProjectMenu() {
      this.isProjectMenuActive = !this.isProjectMenuActive
      this.isChecked = !this.isChecked
    },

    selectProjectType(e) {
      if (e === 'prog') {
        this.modaleIsDisplayed = false
        return (this.currentType = this.allProjects.prog)
      } else if (e === 'integration') {
        this.modaleIsDisplayed = false
        return (this.currentType = this.allProjects.integration)
      } else if (e === 'design') {
        this.modaleIsDisplayed = false
        return (this.currentType = this.allProjects.design)
      } else if (e === 'audiovisuel') {
        this.modaleIsDisplayed = false
        return (this.currentType = this.allProjects.audiovisuel)
      }
    },
  },
}
</script>
