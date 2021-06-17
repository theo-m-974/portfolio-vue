<template>
  <div>
    <Header />

    <full-page :options="options">
      <Home />
      <Projects />
      <About />
      <Competences />
      <Contact />
      <Footer />
    </full-page>
  </div>
</template>

<script>
// import NuxtFullPage from 'nuxt-fullpage.js'
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

  data() {
    return {
      options: {
        licenseKey: 'YOUR_KEY_HERE',
        afterLoad: this.afterLoad,
        scrollBar: false,
        menu: '#menu',
        navigation: true,
        anchors: ['home', 'projects', 'about', 'skills', 'contact', 'footer'],
      },
    }
  },
}
</script>

<style lang="scss">
@import 'assets/scss/style.scss';
</style>
