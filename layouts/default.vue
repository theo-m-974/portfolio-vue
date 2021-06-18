<template>
  <div>
    <client-only>
      <full-page id="fullpage" :options="options">
        <Header />
        <Home />
        <!-- eslint-disable-next-line vue/attribute-hyphenation -->
        <Projects :projectsInViewport="isOnProjectsPage" />
        <About />
        <Competences />
        <Contact />
        <Footer />
      </full-page>
    </client-only>
  </div>
</template>

<script>
// import $ from 'jquery'
import Header from '~/components/Header'
import Home from '~/components/Home'
import Projects from '~/components/Projects'
import About from '~/components/About'
import Competences from '~/components/Competences'
import Contact from '~/components/Contact'
import Footer from '~/components/Footer'

export default {
  components: {
    Header,
    Home,
    Projects,
    About,
    Competences,
    Contact,
    Footer,
  },

  props: {
    projectsInViewport: {
      type: Boolean,
      required: false,
    },
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
        anchors: [
          'home-page',
          'projects-page',
          'about-page',
          'skills-page',
          'contact-page',
          'footer-page',
        ],
      },
      isOnProjectsPage: false,
    }
  },

  // mounted() {},

  methods: {
    afterLoad() {
      if (location.href.includes('#projects-page')) {
        this.isOnProjectsPage = true
      } else {
        this.isOnProjectsPage = false
      }
    },
  },
}
</script>

<style lang="scss">
@import 'assets/scss/style.scss';
</style>
