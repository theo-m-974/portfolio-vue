<template>
  <header id="header" class="header fixed">
    <nav>
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
        <li class="projects--li" @click="displayMenu()">
          <a id="projects-link" href="#projects-page" class="project-nav"
            >Réalisations</a
          >
        </li>
        <li @click="displayMenu()">
          <a href="#about-page" class="about-nav">À propos</a>
        </li>
        <li @click="displayMenu()">
          <a href="#skills-page" class="competences-nav">Compétences</a>
        </li>

        <li @click="displayMenu()">
          <a href="#contact-page" class="contact-nav">Contact</a>
        </li>
      </ul>

      <div class="logo">
        <a href="#home-page">
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
export default {
  name: 'Header',

  props: {
    projectsInViewport: {
      type: Boolean,
      require: true,
    },
  },

  data() {
    return {
      isMenuActive: false,
      isChecked: false,
      isOnHover: false,
    }
  },

  methods: {
    displayMenu() {
      this.isMenuActive = !this.isMenuActive
      this.isChecked = !this.isChecked
    },
  },
}
</script>
