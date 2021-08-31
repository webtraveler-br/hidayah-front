<template>
  <v-app>
    <!-- <v-container> -->
    <banner-home />
    <about-us />
    <services :servicos="servicos" />
    <call-to-action />
    <portfolio :categories="categories" />
    <testimonials :depoimentos="depoimentos" />
    <team />
    <contact />
    <newsletter />
    <!-- </v-container> -->
  </v-app>
</template>

<script>
import BannerHome from '~/components/sections/home/BannerHome'
import AboutUs from '~/components/sections/about/AboutUs'
import Services from '~/components/sections/services/Services'
import CallToAction from '~/components/sections/services/CallToAction'
import Portfolio from '~/components/sections/portfolio/Portfolio'
import Testimonials from '~/components/sections/testimonials/Testimonials'
import Team from '~/components/sections/team/Team'
import Newsletter from '~/components/sections/newsletter/Newsletter'
import Contact from '~/components/sections/contact/Contact'

export default {
  components: {
    BannerHome,
    AboutUs,
    Services,
    CallToAction,
    Portfolio,
    Testimonials,
    Team,
    Newsletter,
    Contact,
  },
  async asyncData({ $axios }) {
    const [servicosRes, categoriesRes, depoimentosRes] = await Promise.all([
      $axios.get('/service'),
      $axios.get('/category'),
      $axios.get('/comment'),
    ])
    return {
      servicos: servicosRes.data.dados,
      categories: categoriesRes.data.message,
      depoimentos: depoimentosRes.data.message,
    }
  },
  data() {
    return {
      categories: [],
    }
  },
}
</script>
