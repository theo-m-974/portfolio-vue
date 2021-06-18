<!-- eslint-disable vue/no-v-html -->
<template>
  <div id="projects" class="projects section">
    <div class="projects-template">
      <!-- <div class="projects-nav">
        <h2>Projets</h2>
        <div class="burger">
          <input
            id="menu_projects_checkbox"
            v-model="isChecked"
            type="checkbox"
            @click="displayProjectMenu()"
          />
          <label for="menu_projects_checkbox">
            <div></div>
            <div></div>
            <div></div>
          </label>
        </div>
        <ul :class="isProjectMenuActive ? 'project-menu-active' : ''">
          <li
            id="prog"
            @click="
              selectType('prog')
              displayProjectMenu()
            "
          >
            <h3 :class="progIsActive ? 'active' : ''">Programmation</h3>
          </li>
          <li
            id="integration"
            @click="
              selectType('integration')
              displayProjectMenu()
            "
          >
            <h3 :class="integrationIsActive ? 'active' : ''">Intégration</h3>
          </li>
          <li
            id="design"
            @click="
              selectType('design')
              displayProjectMenu()
            "
          >
            <h3 :class="designIsActive ? 'active' : ''">Design</h3>
          </li>
          <li
            id="audiovisuel"
            @click="
              selectType('audiovisuel')
              displayProjectMenu()
            "
          >
            <h3 :class="audiovisuelIsActive ? 'active' : ''">Audiovisuel</h3>
          </li>
        </ul>
      </div> -->
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
      <div class="project-modale" :class="modaleIsDisplayed ? 'displayed' : ''">
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
                progIsActive || integrationIsActive ? 'Langages' : 'Logiciels'
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

export default {
  name: 'Projects',

  props: {
    projectsInViewport: {
      type: Boolean,
      required: true,
    },
  },

  data() {
    return {
      allProjects: projects,
      currentType: projects.prog,
      selectedProject: {},
      modaleIsDisplayed: false,
      progIsActive: true,
      integrationIsActive: false,
      designIsActive: false,
      audiovisuelIsActive: false,
      isProjectMenuActive: false,
      isChecked: false,
    }
  },

  mounted() {},

  methods: {
    selectType(e) {
      if (e === 'prog') {
        this.progIsActive = true
        this.integrationIsActive = false
        this.designIsActive = false
        this.audiovisuelIsActive = false
        return (this.currentType = this.allProjects.prog)
      } else if (e === 'integration') {
        this.progIsActive = false
        this.integrationIsActive = true
        this.designIsActive = false
        this.audiovisuelIsActive = false
        return (this.currentType = this.allProjects.integration)
      } else if (e === 'design') {
        this.progIsActive = false
        this.integrationIsActive = false
        this.designIsActive = true
        this.audiovisuelIsActive = false
        return (this.currentType = this.allProjects.design)
      } else if (e === 'audiovisuel') {
        this.progIsActive = false
        this.integrationIsActive = false
        this.designIsActive = false
        this.audiovisuelIsActive = true
        return (this.currentType = this.allProjects.audiovisuel)
      }
    },

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
  },
}
</script>
