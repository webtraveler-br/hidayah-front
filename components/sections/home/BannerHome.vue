<template>
  <div>
    <v-responsive>
      <v-carousel class="carousel-box" hide-delimiter-background continuous>
        <v-carousel-item
          v-for="(item, i) in items"
          :key="i"
          transition="fade-transition"
          reverse-transition="fade-transition"
          :src="require('~/' + item.src + '.jpg')"
          :alt="item.alt"
          gradient="to top right, rgba(0.75,0.75,0.75,0.75), rgba(0.75,0.75,0.75,0.75)"
          class="bannerDiv"
        >
          <div class="bannerDiv">
            <p class="titleSt">
              {{ item.title }}
            </p>
            <p class="descriptionSt text-center">
              Ut velit est quam dolor ad a aliquid qui aliquid. Sequi ea ut et
              est quaerat sequi nihil ut aliquam. Occaecati alias dolorem
              mollitia ut. Similique ea voluptatem. Esse doloremque accusamus
              repellendus deleniti vel. Minus et tempore modi architecto.
            </p>
            <button class="button">Read More</button>
          </div>
        </v-carousel-item>
      </v-carousel>
    </v-responsive>
  </div>
</template>
<script>
export default {
  name: 'BannerHome',
  data() {
    return {
      items: [
        {
          src: 'static/imagens/slide/slide-1',
          title: 'Welcome to Hidayah',
          alt: 'Escritório de trabalho',
        },
        {
          src: 'static/imagens/slide/slide-2',
          title: 'Lorem Ipsum Dolor',
          alt: 'Sala de reuniões com uma mesa e cadeiras',
        },
        {
          src: 'static/imagens/slide/slide-3',
          title: 'Sequi ea ut et est quaerat',
          alt: 'Amigos sentados em uma mesa',
        },
      ],
    }
  },
}
</script>
<style scoped>
.v-carousel >>> .v-window__prev {
  height: 55px;
  width: 55px;
  color: rgb(66, 68, 68);
}
.v-carousel >>> .v-btn {
  height: 55px;
  width: 55px;
  color: rgba(255, 255, 255, 0.4);
  background-color: rgba(255, 255, 255, 0.1);
}
.v-carousel >>> .v-carousel__controls__item {
  height: 10px;
  width: 10px;
  color: #fff;
  background-color: transparent !important;
  margin-inline: 5px;
}

.v-carousel >>> .v-btn--active {
  color: rgb(92, 181, 255);
}

.carousel-box {
  height: 100vh !important;
}

.titleSt {
  font-family: 'Raleway', sans-serif;
  font-weight: 600;
  font-size: 47px;
  margin-top: 9vh;
  text-align: center;
}
.descriptionSt {
  margin-top: 1px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
  font-size: 15px;
  padding-inline: 18vw;
}
.bannerDiv {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
.button {
  background-color: #428bca;
  padding-block: 10px;
  padding-inline: 33px;
  margin-top: 15px;
  font-size: 15px;
  border-radius: 5px;
  margin-top: 10px;
  font-family: 'Raleway', sans-serif;
}

@media screen and (max-width: 770px) {
  .titleSt {
    font-size: 30px;
    padding-inline: 70px;
  }
  .descriptionSt {
    margin-inline: 20px;
  }
}
</style>
