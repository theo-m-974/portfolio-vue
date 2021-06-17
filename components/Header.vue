<template>
  <header class="header fixed">
    <nav id="header">
      <div class="burger">
        <input
          id="menu_checkbox"
          v-model="isChecked"
          type="checkbox"
          @click="displayMenu()"
        />
        <label for="menu_checkbox">
          <div></div>
          <div></div>
          <div></div>
        </label>
      </div>
      <ul
        id="menu"
        class="navigation--list"
        :class="isMenuActive ? 'active' : ''"
      >
        <li @click="displayMenu()">
          <a
            href="#projects-anchor"
            class="project-nav"
            :class="projectIsActive ? 'nav-active' : ''"
            >Réalisations</a
          >
        </li>
        <li @click="displayMenu()">
          <a
            href="#about"
            class="about-nav"
            :class="aboutIsActive ? 'nav-active' : ''"
            >À propos</a
          >
        </li>
        <li @click="displayMenu()">
          <a
            href="#competences"
            class="competences-nav"
            :class="aboutIsActive ? 'nav-active' : ''"
            >Compétences</a
          >
        </li>

        <li @click="displayMenu()">
          <a
            href="#contact"
            class="contact-nav"
            :class="contactIsActive ? 'nav-active' : ''"
            >Contact</a
          >
        </li>
      </ul>

      <div class="logo">
        <a href="#home">
          <svg
            id="calque_1"
            data-name="calque 1"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 493.43 218.91"
          >
            <defs>
              <style>
                .cls-1 {
                  stroke: #333;
                  stroke-miterlimit: 10;
                  stroke-width: 2px;
                }
              </style>
            </defs>
            <path
              class="cls-1"
              d="M1104.21,538.45l103,102.27.07-212.42Z"
              transform="translate(-714.9 -425.77)"
            />
            <path
              class="cls-1"
              d="M991.58,534.67l106.09,106.09.71-102.38L991.58,428.3Z"
              transform="translate(-714.9 -425.77)"
            />
            <path
              class="cls-1"
              d="M991.58,542.45v99.81l49.9-49.9Z"
              transform="translate(-714.9 -425.77)"
            />
            <path
              class="cls-1"
              d="M793.89,502.24l-1.22,139,71.06-71.06V432.4Z"
              transform="translate(-714.9 -425.77)"
            />
            <path
              class="cls-1"
              d="M869.57,533V428.3h104.7Z"
              transform="translate(-714.9 -425.77)"
            />
            <path
              class="cls-1"
              d="M786.3,502H715.93l0-73.71H860Z"
              transform="translate(-714.9 -425.77)"
            /></svg
        ></a>
      </div>

      <ul class="social-medias--list">
        <li>
          <a href="https://github.com/theo-m-974" target="_blank"
            ><img src="@/assets/img/icons/social/github_black.svg" alt=""
          /></a>
        </li>
        <li>
          <a
            href="https://www.linkedin.com/in/th%C3%A9o-moyano-4b384b1ba/"
            target="_blank"
            ><img src="@/assets/img/icons/social/linkedin_black.svg" alt=""
          /></a>
        </li>
      </ul>
    </nav>
  </header>
</template>
<script>
import $ from 'jquery'

export default {
  name: 'Header',

  data() {
    return {
      isMenuActive: false,
      projectIsActive: false,
      aboutIsActive: false,
      contactIsActive: false,
      homeIsActive: true,
      isChecked: false,
    }
  },

  mounted() {
    const projectsContainer = $('#projects')
    const projectsOffsetTop = projectsContainer.position().top

    const aboutContainer = $('#about')
    const aboutOffsetTop = aboutContainer.position().top

    const contactContainer = $('#contact')
    const contactOffsetTop = contactContainer.position().top

    const homeContainer = $('#home')
    const homeOffsetTop = homeContainer.position().top

    const competencesContainer = $('#competences')
    const competencesOffsetTop = competencesContainer.position().top

    document.addEventListener('scroll', function () {
      // if inférieur a projet et supérieur à home
      if (
        window.scrollY <= projectsOffsetTop &&
        window.scrollY >= homeOffsetTop
      ) {
        $('.project-nav').removeClass('nav-active')
        $('.about-nav').removeClass('nav-active')
        $('.contact-nav').removeClass('nav-active')
        this.projectIsActive = false
        this.aboutIsActive = false
        this.contactIsActive = false
        this.homeIsActive = true
      }
      // if inférieur a about et supérieur à home
      else if (
        window.scrollY <= aboutOffsetTop &&
        window.scrollY >= homeOffsetTop
      ) {
        $('.project-nav').addClass('nav-active')
        $('.about-nav').removeClass('nav-active')
        $('.contact-nav').removeClass('nav-active')
        this.projectIsActive = true
        this.aboutIsActive = false
        this.contactIsActive = false
        this.homeIsActive = false
      }
      // if inférieur a contact et supérieur à projet
      else if (
        window.scrollY <= contactOffsetTop &&
        window.scrollY >= projectsOffsetTop
      ) {
        $('.project-nav').removeClass('nav-active')
        $('.about-nav').addClass('nav-active')
        $('.contact-nav').removeClass('nav-active')
        this.projectIsActive = false
        this.aboutIsActive = false
        this.contactIsActive = true
        this.homeIsActive = false
      }
      // if supérieur à competences
      else if (window.scrollY >= competencesOffsetTop) {
        $('.project-nav').removeClass('nav-active')
        $('.about-nav').removeClass('nav-active')
        $('.contact-nav').addClass('nav-active')
        this.projectIsActive = false
        this.aboutIsActive = true
        this.contactIsActive = false
        this.homeIsActive = false
      }
    })
  },

  methods: {
    displayMenu() {
      this.isMenuActive = !this.isMenuActive
      this.isChecked = !this.isChecked
    },
  },
}
</script>
