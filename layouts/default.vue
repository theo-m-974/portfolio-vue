<template>
  <div>
    <client-only>
      <full-page id="fullpage" ref="fullpage" :options="options">
        <!-- eslint-disable-next-line vue/attribute-hyphenation -->
        <Header :projects-in-viewport="isOnProjectsPage" />
        <Home />
        <Projects />
        <!-- <Project-Template /> -->
        <About />
        <Competences />
        <Contact />
        <Footer />
      </full-page>
    </client-only>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import $ from 'jquery'
import Header from '~/components/Header'
import Home from '~/components/Home'
import Projects from '~/components/Projects'
// import ProjectTemplate from '~/components/Project-Template'
import About from '~/components/About'
import Competences from '~/components/Competences'
import Contact from '~/components/Contact'
import Footer from '~/components/Footer'

export default {
  components: {
    Header,
    Home,
    Projects,
    // ProjectTemplate,
    About,
    Competences,
    Contact,
    Footer,
  },

  data() {
    return {
      options: {
        licenseKey: '2BEE1756-492F4AB1-84F9CB4E-CD8BE6E1',
        afterLoad: this.afterLoad,
        scrollBar: false,
        menu: '#header',
        fixedElements: '#header',
        navigation: true,
        scrollOverflow: true,
        autoscrolling: true,
        anchors: [
          'home-page',
          'projects-page',
          // 'project-template-page',
          'about-page',
          'skills-page',
          'contact-page',
          'footer-page',
        ],
        loopTop: true,
        loopBottom: true,
        fitToSection: true,
        // normalScrollElements: '#modale',
        // scrollOverflowReset: true,
      },

      isOnProjectsPage: false,
    }
  },

  methods: {
    afterLoad() {
      if (location.href.includes('#projects-page')) {
        this.isOnProjectsPage = true
        // this.$refs.fullpage.api.setAllowScrolling(false)
      } else {
        this.isOnProjectsPage = false
        // this.$refs.fullpage.api.setAllowScrolling(true)
      }
    },
  },
}
</script>

<style lang="scss">
@import 'assets/scss/style.scss';
</style>
