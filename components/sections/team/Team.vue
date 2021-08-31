<template>
  <v-container fluid>
    <div class="team">
      <v-row class="header-team pb-10 px-3" justify="center" align="center">
        <v-col class="header-team-rounded" align="center" cols="12">
          <h2>Team</h2>
        </v-col>
        <v-col class="header-team-title my-0 pa-0" align="center" cols="12">
          <h3>Our Hard Working <span>Team</span></h3>
        </v-col>
        <v-col
          class="header-team-description mt-2 mb-0 py-0 px-3"
          align="center"
          cols="12"
        >
          <span>
            Ut possimus qui ut temporibus culpa velit eveniet modi omnis est
            adipisci expedita at voluptas atque vitae autem.
          </span>
        </v-col>
      </v-row>
      <v-row class="team-cards" justify="center" align="center">
        <v-col
          v-for="equipe in equipes"
          :key="equipe.name"
          class="team-img-box ma-0 pa-0"
          cols="12"
          xl="3"
          lg="3"
          md="6"
          sm="6"
          justify="center"
          align="center"
        >
          <v-hover v-slot:default="{ hover }">
            <v-card class="team-img" flat>
              <!-- <v-img :src="path + equipe.imagem.caminho" /> -->
              <v-img :src="require('~/' + equipe.src + '.jpg')">
                <v-col v-if="hover" class="team-img-hover">
                  <div class="img-hover-text">
                    <h4>{{ equipe.name }}</h4>
                    <p>{{ equipe.job }}</p>
                  </div>
                  <div class="img-hover-social">
                    <a href="/"><v-icon>mdi-twitter</v-icon></a>
                    <a href="/"><v-icon>mdi-facebook</v-icon></a>
                    <a href="/"><v-icon>mdi-instagram</v-icon></a>
                    <a href="/"><v-icon>mdi-linkedin</v-icon></a>
                  </div>
                </v-col>
              </v-img>
            </v-card>
          </v-hover>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
export default {
  // props: {
  //   equipe: {
  //     type: Array,
  //     requeried: true,
  //     default: () => {},
  //   },
  // },
  data() {
    return {
      // path: 'http://127.0.0.1:8000/',
      equipes: [
        {
          name: 'Walter White',
          job: 'Chief Executive Officer',
          src: 'static/imagens/team/team-1',
        },
        {
          name: 'Sarah Jhonson',
          job: 'Product Manager',
          src: 'static/imagens/team/team-2',
        },
        {
          name: 'William Anderson',
          job: 'CTO',
          src: 'static/imagens/team/team-3',
        },
        {
          name: 'Amanda Jepson',
          job: 'Accountant',
          src: 'static/imagens/team/team-4',
        },
      ],
    }
  },
}
</script>

<style scoped>
.container {
  padding: 0;
}
.team {
  margin: 80px 90px;
}
.header-team-rounded h2 {
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
.header-team-title h3 {
  font-family: 'Raleway', sans-serif;
  font-size: 32px;
  font-weight: 700;
  color: #444444;
}
.header-team-title span {
  color: #353b41;
}
.header-team-description {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  font-weight: 500;
  color: #919191;
}
.team-img {
  height: 240px;
  width: 240px;
  padding: 5px;
}
.team-img-hover {
  background: linear-gradient(
    0deg,
    #000000e6 0%,
    #000000cc 20%,
    #00d4ff00 100%
  );
  display: flex;
  opacity: 1;
  height: 240px;
  width: 240px;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
}
.img-hover-text h4 {
  font-family: 'Raleway', sans-serif;
  font-size: 18px;
  font-weight: 700;
  color: #fff;
  margin-bottom: 2px;
}
.img-hover-text p {
  font-family: 'Open Sans', sans-serif;
  font-size: 13px;
  font-weight: 400;
  font-style: italic;
  color: #fff;
  margin-bottom: 0px;
}
.img-hover-social .v-icon {
  color: #fff;
  font-size: 20px;
  margin: 10px;
}
.img-hover-social a {
  text-decoration: none;
}
.img-hover-social .v-icon:hover {
  color: #428bca;
}
@media screen and (max-width: 1264px) {
  .team {
    margin: 50px 0;
  }
  .team-img {
    height: 350px;
    width: 350px;
  }
  .team-img-hover {
    height: 350px;
    width: 350px;
  }
  .img-hover-social .v-icon {
    font-size: 26px;
    margin: 15px;
  }
}
@media screen and (max-width: 750px) {
  .team-img {
    height: 300px;
    width: 300px;
  }
  .team-img-hover {
    height: 300px;
    width: 300px;
  }
}
@media screen and (max-width: 598px) {
  .team-img {
    height: 350px;
    width: 350px;
  }
  .team-img-hover {
    height: 350px;
    width: 350px;
  }
}
</style>
