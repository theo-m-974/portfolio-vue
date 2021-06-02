<template>
  <div>
    <Header />
    <Home />
    <Projects />
    <About />
    <Competences />
    <Contact />
    <Footer />
  </div>
</template>

<script>
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
}
</script>

<style lang="scss">
@import 'assets/scss/style.scss';
</style>
