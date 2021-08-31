<template>
  <div>
    <div class="header-box">
      <span class="header-text">
        PORTFOLIO
      </span>
      <div class="title-box">
        <span class="title-text">Check our </span>
        <span class="title-text" style="color: #428bca;">Portfolio</span>
      </div>
      <span class="description-text"
        >Ut possimus qui ut temporibus culpa velit eveniet modi omnis est
        adipisci expedita at voluptas atque vitae autem.</span
      >
    </div>
    <div class="categories-box">
      <v-btn-toggle
        v-model="selectedCategory"
        class="category-btns"
        borderless
        mandatory
        tile
      >
        <v-btn class="category-btn" text>ALL</v-btn>
        <v-btn
          v-for="category in categories"
          :key="category"
          class="category-btn"
          text
          >{{ category.nome }}</v-btn
        >
      </v-btn-toggle>
    </div>
    <v-row class="portfolio-box" no-gutters>
      <v-col lg="3" md="6" sm="12" class="portfolio-col" align-self="start">
        <v-row
          v-for="portfolio in portfoliosCol(1)"
          :key="portfolio"
          class="ma-0 pa-0"
          no-gutters
        >
          <v-hover v-slot:default="{ hover }" class="port-wrapper">
            <v-img
              :src="path + portfolio.imagem.caminho"
              :gradient="
                hover
                  ? 'to top right, rgba(0.45,0.45,0.45,0.45), rgba(0.45,0.45,0.45,0.45)'
                  : ''
              "
              class="image-port"
            >
              <div v-if="hover" class="card-box">
                <span class="title-card">{{ portfolio.titulo }}</span>
                <span class="description-card">{{
                  categories[portfolio.pivot.categoria_id - 1].nome
                }}</span>
                <div class="card-icons">
                  <a :href="path + portfolio.imagem.caminho" target="_blank">
                    <v-icon class="icon-card">mdi-plus</v-icon>
                  </a>
                  <a :href="portfolio.link" target="_blank">
                    <v-icon class="icon-card">mdi-link-variant</v-icon>
                  </a>
                </div>
              </div>
            </v-img>
          </v-hover>
        </v-row>
      </v-col>
      <v-col lg="3" md="6" sm="12" class="portfolio-col" align-self="start">
        <v-row
          v-for="portfolio in portfoliosCol(2)"
          :key="portfolio"
          class="ma-0 pa-0"
          no-gutters
        >
          <v-hover v-slot:default="{ hover }" class="port-wrapper">
            <v-img
              :src="path + portfolio.imagem.caminho"
              :gradient="
                hover
                  ? 'to top right, rgba(0.45,0.45,0.45,0.45), rgba(0.45,0.45,0.45,0.45)'
                  : ''
              "
              class="image-port"
            >
              <div v-if="hover" class="card-box">
                <span class="title-card">{{ portfolio.titulo }}</span>
                <span class="description-card">{{
                  categories[portfolio.pivot.categoria_id - 1].nome
                }}</span>
                <div class="card-icons">
                  <a :href="path + portfolio.imagem.caminho" target="_blank">
                    <v-icon class="icon-card">mdi-plus</v-icon>
                  </a>
                  <a :href="portfolio.link" target="_blank">
                    <v-icon class="icon-card">mdi-link-variant</v-icon>
                  </a>
                </div>
              </div>
            </v-img>
          </v-hover>
        </v-row>
      </v-col>
      <v-col lg="3" md="6" sm="12" class="portfolio-col" align-self="start">
        <v-row
          v-for="portfolio in portfoliosCol(3)"
          :key="portfolio"
          class="ma-0 pa-0"
          no-gutters
        >
          <v-hover v-slot:default="{ hover }" class="port-wrapper">
            <v-img
              :src="path + portfolio.imagem.caminho"
              :gradient="
                hover
                  ? 'to top right, rgba(0.45,0.45,0.45,0.45), rgba(0.45,0.45,0.45,0.45)'
                  : ''
              "
              class="image-port"
            >
              <div v-if="hover" class="card-box">
                <span class="title-card">{{ portfolio.titulo }}</span>
                <span class="description-card">{{
                  categories[portfolio.pivot.categoria_id - 1].nome
                }}</span>
                <div class="card-icons">
                  <a :href="path + portfolio.imagem.caminho" target="_blank">
                    <v-icon class="icon-card">mdi-plus</v-icon>
                  </a>
                  <a :href="portfolio.link" target="_blank">
                    <v-icon class="icon-card">mdi-link-variant</v-icon>
                  </a>
                </div>
              </div>
            </v-img>
          </v-hover>
        </v-row>
      </v-col>
      <v-col lg="3" md="6" sm="12" class="portfolio-col" align-self="start">
        <v-row
          v-for="portfolio in portfoliosCol(4)"
          :key="portfolio"
          class="ma-0 pa-0"
          no-gutters
        >
          <v-hover v-slot:default="{ hover }" class="port-wrapper">
            <v-img
              :src="path + portfolio.imagem.caminho"
              :gradient="
                hover
                  ? 'to top right, rgba(0.45,0.45,0.45,0.45), rgba(0.45,0.45,0.45,0.45)'
                  : ''
              "
              class="image-port"
            >
              <div v-if="hover" class="card-box">
                <span class="title-card">{{ portfolio.titulo }}</span>
                <span class="description-card">{{
                  categories[portfolio.pivot.categoria_id - 1].nome
                }}</span>
                <div class="card-icons">
                  <a :href="path + portfolio.imagem.caminho" target="_blank">
                    <v-icon class="icon-card">mdi-plus</v-icon>
                  </a>
                  <a :href="portfolio.link" target="_blank">
                    <v-icon class="icon-card">mdi-link-variant</v-icon>
                  </a>
                </div>
              </div>
            </v-img>
          </v-hover>
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  props: {
    categories: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
  data() {
    return {
      selectedCategory: 0,
      path: 'http://127.0.0.1:8000/',
    }
  },
  computed: {
    portfoliosFunct() {
      let portfolios = []
      let cont = 1
      if (this.selectedCategory === 0) {
        portfolios = []
        this.categories.forEach(function (item) {
          if (item.portifolios.length) {
            item.portifolios.forEach(function (port) {
              if (cont === 5) cont = 1
              port = { port, col: cont }
              portfolios.push(port)
              cont++
            })
          }
        })
      } else if (this.categories[this.selectedCategory - 1].portifolios.length)
        this.categories[this.selectedCategory - 1].portifolios.forEach(
          function (port) {
            if (cont === 5) cont = 1
            port = { port, col: cont }
            portfolios.push(port)
            cont++
          }
        )
      return portfolios
    },
  },
  methods: {
    portfoliosCol(col) {
      let portfolios = []
      portfolios = this.portfoliosFunct
      portfolios = portfolios.filter(function (item) {
        return item.col === col
      })
      const portfoliosRes = []
      portfolios.forEach(function (item) {
        portfoliosRes.push(item.port)
      })
      return portfoliosRes
    },
  },
}
</script>
<style scoped>
.header-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 265px;
}
.categories-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 50px;
}
.portfolio-box {
  display: flex;
  flex-direction: row;
  justify-content: flex-start !important;
  margin-inline: 120px;
}
.portfolio-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start !important;
  padding-inline: 0px !important;
}
.port-wrapper {
  margin-bottom: 25px;
  height: auto;
}
.header-text {
  font-family: 'Raleway', sans-serif;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 1px;
  padding: 8px 20px;
  color: #428bca;
  background: #f5f9fc;
  border-radius: 50px;
  margin-top: 80px;
  margin-bottom: 13px;
}
.title-text {
  font-family: 'Raleway', sans-serif;
  font-size: 32px;
  font-weight: 700;
  color: #444444;
}
.description-text {
  font-family: 'Open Sans', sans-serif;
  font-weight: 500;
  font-size: 16px;
  color: #919191;
  margin-top: 13px;
  text-align: center;
}
.category-btn {
  font-size: 14px;
  font-weight: 600;
  line-height: 1;
  letter-spacing: normal;
  font-family: 'Open Sans', sans-serif;
  height: 32px !important;
  width: 55px !important;
  border-radius: 4px !important;
  margin-inline: 2px !important;
}
.v-item--active {
  color: #ffffff !important;
  background-color: #428bca !important;
}
.image-port {
  /* width: 370px; */
  width: 20vw;
  height: auto;
}
.card-box {
  display: flex;
  height: 100%;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-end;
  margin-left: 15px;
}
.card-icons {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 25px;
  margin-top: 5px;
}
.title-card {
  font-family: 'Raleway', sans-serif;
  font-size: 20px;
  color: #ffffff;
  font-weight: 600;
  line-height: 1.2;
  margin-bottom: 8px;
}
.description-card {
  font-family: 'Open Sans', sans-serif;
  color: rgba(255, 255, 255, 0.7);
  font-size: 14px;
  text-transform: uppercase;
  padding: 0;
  margin: 0;
  font-style: italic;
}
.icon-card {
  color: #ffffff;
  font-size: 26px;
  margin-inline: 4px;
}

@media screen and (max-width: 1264px) {
  .image-port {
    width: 360px;
  }
}
@media screen and (max-width: 335px) {
  .card-box {
    margin-left: 20px;
  }
}
</style>
