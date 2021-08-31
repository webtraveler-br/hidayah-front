<template>
  <v-container fluid>
    <v-row class="text-services" justify="center" align="center">
      <v-col class="text-services-rounded" align="center" cols="12">
        <h2>Services</h2>
      </v-col>
      <v-col class="text-services-title my-0 pa-0" align="center" cols="12">
        <h3>Check Our <span>Services</span></h3>
      </v-col>
      <v-col
        class="text-services-description mt-2 mb-0 py-0 px-3"
        align="center"
        cols="12"
      >
        <span>
          Ut possimus qui ut temporibus culpa velit eveniet modi omnis est
          adipisci expedita at voluptas atque vitae autem.
        </span>
      </v-col>
    </v-row>
    <v-row class="services" justify="center" align="center">
      <v-col
        v-for="servico in servicos"
        :key="servico.title"
        cols="12"
        xl="4"
        lg="4"
        md="6"
        sm="6"
      >
        <div class="services-box">
          <div class="services-icon">
            <v-icon>{{ servico.icon }}</v-icon>
          </div>
          <div class="services-title">
            <h4>
              <a href="">{{ servico.title }}</a>
            </h4>
          </div>
          <div class="services-description">
            <p>{{ servico.description }}</p>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: {
    servicos: {
      type: Array,
      requeried: true,
      default: () => {},
    },
  },
  data() {
    return {}
  },
}
</script>

<style scoped>
.text-services {
  padding-top: 50px;
  padding-bottom: 50px;
}
.text-services-rounded h2 {
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
.text-services-title h3 {
  font-family: 'Raleway', sans-serif;
  font-size: 32px;
  font-weight: 700;
  color: #444444;
}
.text-services-title span {
  color: #428bca;
}
.text-services-description {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  font-weight: 500;
  color: #919191;
}
.services {
  margin-bottom: 30px;
  padding: 0 70px;
}
.services-box {
  margin-bottom: 40px;
}
.services-icon {
  display: inline-flex;
  float: left;
}
.services-icon .v-icon {
  color: #428bca;
  font-size: 36px;
  line-height: 1;
}
.services-title h4 {
  font-family: 'Raleway', sans-serif;
  font-size: 18px;
  font-weight: 700;
  margin-left: 60px;
  margin-bottom: 15px;
}
.services-title a {
  text-decoration: none;
  color: #444444;
}
.services-title a:hover {
  color: #428bca;
}
.services-description {
  font-family: 'Open Sans', sans-serif;
  font-size: 14px;
  font-weight: 400;
  margin-left: 60px;
  color: #444444;
  display: block;
}
@media screen and (max-width: 960px) {
  .services {
    padding: 0 15px;
  }
}
</style>
