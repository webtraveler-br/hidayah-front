<template>
  <v-container fluid>
    <div class="testimonials">
      <v-row
        class="header-testimonials pb-10 px-3"
        justify="center"
        align="center"
      >
        <v-col class="header-testimonials-rounded" align="center" cols="12">
          <h2>Testimonials</h2>
        </v-col>
        <v-col
          class="header-testimonials-title my-0 pa-0"
          align="center"
          cols="12"
        >
          <h3>What They <span>Are Saying </span>About Us</h3>
        </v-col>
        <v-col
          class="header-testimonials-description mt-2 mb-0 py-0 px-3"
          align="center"
          cols="12"
        >
          <span>
            Ut possimus qui ut temporibus culpa velit eveniet modi omnis est
            adipisci expedita at voluptas atque vitae autem.
          </span>
        </v-col>
      </v-row>
      <v-row class="card-testimonials" justify="center" align="center">
        <v-col
          v-for="depoimento in depoimentos"
          :key="depoimento.nome"
          cols="10"
          xl="6"
          lg="6"
        >
          <v-card class="card-testimonials-box mx-2" elevation="2" tile>
            <div class="card-testimonials-content pa-10">
              <div class="card-testimonials-image mr-3">
                <v-img :src="path + depoimento.imagem.caminho" />
              </div>
              <h3 class="card-testimonials-name mt-2">
                {{ depoimento.nome }}
              </h3>
              <h4 class="card-testimonials-career mt-1">
                {{ depoimento.emprego }}
              </h4>
              <p class="card-testimonials-comment mt-4 mb-0">
                <v-icon>mdi-format-quote-open</v-icon>
                {{ depoimento.comentario }}
                <v-icon>mdi-format-quote-close</v-icon>
              </p>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
export default {
  props: {
    depoimentos: {
      type: Array,
      requeried: true,
      default: () => {},
    },
  },
  data() {
    return {
      path: 'http://127.0.0.1:8000/',
    }
  },
}
</script>

<style scoped>
.container {
  background-color: #fafafb;
  padding: 0;
}
.testimonials {
  padding: 80px 100px;
}
.header-testimonials-rounded h2 {
  font-family: 'Raleway', sans-serif;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 1px;
  text-transform: uppercase;
  background: #f5f9fc;
  border-radius: 50px;
  color: #428bca;
  padding: 8px 20px;
  display: inline-block;
  margin: 0;
}
.header-testimonials-title h3 {
  font-family: 'Raleway', sans-serif;
  font-size: 32px;
  font-weight: 700;
  color: #444444;
}
.header-testimonials-title span {
  color: #428bca;
}
.header-testimonials-description {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  font-weight: 500;
  color: #919191;
}
.card-testimonials-image {
  width: 90px;
  border: 6px solid #fff;
  float: left;
}
.card-testimonials-image >>> .v-image__image {
  border-radius: 10px !important;
}
.card-testimonials-name h3 {
  font-family: 'Raleway', sans-serif;
  font-size: 18px;
  font-weight: 700;
  color: #394047;
}
.card-testimonials-career {
  font-family: 'Raleway', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #999;
}
.card-testimonials-comment {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  font-weight: 400;
  font-style: italic;
  color: #444;
}
.card-testimonials-comment .v-icon {
  display: inline-block;
  position: relative;
  color: #b9d4ec;
  font-size: 26px;
}
@media screen and (max-width: 960px) {
  .testimonials {
    padding: 50px 0;
  }
  .card-testimonials-box {
    margin: 0;
  }
}
</style>
