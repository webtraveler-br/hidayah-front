<template>
  <v-container fluid>
    <v-row class="about" justify="center" align="center">
      <v-col class="about-img-block" cols="12" xl="6" lg="6">
        <!-- <a
          class="venobox"
          data-vbtype="video"
          href="https://www.youtube.com/watch?v=jDDaplaOz7Q&feature=emb_logo"
        >
        </a> -->
        <div class="about-img-item">
          <a
            href="https://www.youtube.com/watch?v=jDDaplaOz7Q&feature=emb_logo"
          >
            <v-btn class="about-img-btn" depressed icon>
              <v-icon>mdi-play</v-icon>
            </v-btn>
          </a>
        </div>
      </v-col>
      <v-col class="about-text" cols="12" lg="6">
        <div class="about-title">
          <h3>
            Enim quis est voluptatibus aliquid consequatur fugiat
          </h3>
        </div>
        <div class="about-title-description">
          <p>
            Esse voluptas cumque vel exercitationem. Reiciendis est hic
            accusamus. Non ipsam et sed minima temporibus laudantium. Soluta
            voluptate sed facere corporis dolores excepturi. Libero laboriosam
            sint et id nulla tenetur. Suscipit aut voluptate.
          </p>
        </div>
        <div
          v-for="section in sections"
          :key="section.title"
          class="about-section"
          description
          icon
        >
          <div class="about-section-icon-box">
            <v-btn depressed icon absolute d-block>
              <div>
                <v-icon class="about-section-icon"> {{ section.icon }} </v-icon>
              </div>
            </v-btn>
          </div>
          <div class="about-section-title">
            <h4>{{ section.title }}</h4>
          </div>
          <div class="about-section-description">
            <p>{{ section.description }}</p>
          </div>
        </div>
      </v-col>
    </v-row>
    <v-row class="skills" justify="center" align="center">
      <v-col
        v-for="progress in bars"
        :key="progress.title"
        class="skills-progress"
        number
        cols="12"
        xl="6"
        lg="6"
      >
        <div class="skills-progress-text">
          <span> {{ progress.title }}</span>
          <span> {{ progress.number }}</span>
        </div>
        <div class="skills-progress-value">
          <v-progress-linear :value="progress.number" />
        </div>
      </v-col>
    </v-row>
    <v-row class="count" justify="center" align="center">
      <v-col
        v-for="count in numbers"
        :key="count.number"
        text
        cols="6"
        xl="3"
        lg="3"
      >
        <div class="count-number">
          <span>{{ count.number }}</span>
        </div>
        <div class="count-text">
          <p>{{ count.text }}</p>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// import $ from 'jquery'

export default {
  //   mounted() {
  //     $('.venobox').venobox()
  //   },
  data() {
    return {
      sections: [
        {
          title: 'Lorem Ipsum',
          description:
            'Voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident',
          icon: 'mdi-fingerprint',
        },
        {
          title: 'Nemo Enim',
          description:
            'At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque',
          icon: 'mdi-gift-outline',
        },
        {
          title: 'Dine Pad',
          description:
            'Explicabo est voluptatum asperiores consequatur magnam. Et veritatis odit. Sunt aut deserunt minus aut eligendi omnis',
          icon: 'mdi-atom',
        },
      ],
      bars: [
        { title: 'HTML', number: '100%' },
        { title: 'PHP', number: '80%' },
        { title: 'CSS', number: '90%' },
        { title: 'WordPress/CMS', number: '90%' },
        { title: 'JavaScript', number: '75%' },
        { title: 'Photoshop', number: '55%' },
      ],
      numbers: [
        { number: '232', text: 'Clients' },
        { number: '521', text: 'Projects' },
        { number: '1,463', text: 'Hours of Support' },
        { number: '15', text: 'Hard Workers' },
      ],
    }
  },
}
</script>

<style scoped>
.about {
  margin: 80px;
}
.about-img-block {
  background-image: url('../../../static/imagens/about.jpg');
  background-position: center;
  background-size: cover;
  display: flex;
  height: 793px;
  padding: 15px 0;
  align-items: center;
  justify-content: center;
}
.about-img-btn {
  width: 94px;
  height: 94px;
  background: radial-gradient(#428bca 50%, #428bca66 52%);
  border-radius: 50%;
  display: flex;
}
.about-img-btn .v-icon {
  color: white;
}
.about-text {
  display: inline-block;
  padding: 48px;
}
.about-title {
  font-family: 'Raleway', sans-serif;
  font-size: 28px;
  font-weight: 700;
  color: #394047;
  margin-bottom: 15px;
}
.about-title-description {
  font-family: 'Open Sans', sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #444444;
  margin-bottom: 1rem;
}
.about-section {
  margin-top: 40px;
}
.about-section-icon-box {
  background: transparent;
  border-color: #428bca;
  float: left;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 64px;
  height: 64px;
  border: 2px solid #b9d4ec;
  border-radius: 50px;
}
.about-section-icon-box:hover {
  background-color: #428bca;
}
.about-section >>> .about-section-icon {
  color: #428bca;
  display: flex;
  font-size: 35px;
  justify-content: center;
}
.about-section-icon:hover {
  color: white;
}
.about-section-title {
  font-family: 'Raleway', sans-serif;
  font-size: 18px;
  font-weight: 700;
  line-height: 1.2;
  color: #343a40;
  margin-left: 22px;
  margin-bottom: 10px;
  display: inline-block;
}
.about-section-description {
  font-family: 'Open Sans', sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 24px;
  margin-left: 85px;
  font-size: 14px;
  margin-bottom: 1rem;
  display: block;
}
.skills {
  margin: 0 80px 80px 80px;
}
.skills-progress {
  height: 50px;
}
.skills-progress-text {
  font-family: 'Poppins', sans-serif;
  font-size: 12px;
  font-weight: 600;
  padding: 10px 0;
  text-transform: uppercase;
  color: #394047;
  justify-content: space-between;
  display: flex;
}
.skills-progress-value >>> .v-progress-linear {
  height: 10px !important;
  transition: 0.9s;
}
.skills-progress-value >>> .v-progress-linear__determinate.primary {
  background-color: #428bca !important;
}
.skills-progress-value >>> .v-progress-linear__background {
  background-color: #e3e6e9 !important;
}
.count {
  padding: 80px 0 60px 0;
  background-color: #fafafb;
}
.count-number {
  font-family: 'Open Sans', sans-serif;
  font-size: 48px;
  font-weight: 700;
  color: #428bca;
  display: flex;
  justify-content: center;
}
.count-text {
  font-family: 'Raleway', sans-serif;
  font-size: 15px;
  font-weight: 500;
  margin-bottom: 20px;
  display: flex;
  justify-content: center;
}
@media screen and (max-width: 960px) {
  .about {
    margin: 30px 0;
  }
  .skills {
    margin: 80px 0;
  }
  .about-img-block {
    height: 500px;
  }
  .about-text {
    padding: 30px 15px 6px 6px;
  }
}
</style>
