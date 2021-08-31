<template>
  <v-app>
    <nuxt />
    <v-app-bar max-height="70px" color="#171a1dcc" flat fixed class="nav-bar">
      <v-spacer />
      <spam class="nav-title"> Hidayah </spam>
      <v-spacer />
      <v-spacer />
      <v-spacer />

      <div v-for="btn in btns" :key="btn.title" link>
        <div v-if="[btn.title] == 'Drop Down'">
          <v-menu offset-y down>
            <template v-slot:activator="{ on }">
              <v-btn
                class="nav-link hidden-md-and-down nav-btn"
                depressed
                text
                v-on="on"
              >
                <spam>Drop Down</spam>
                <v-icon>mdi-chevron-down</v-icon>
              </v-btn>
            </template>
            <v-list>
              <v-list-item v-for="dropdown in drops" :key="dropdown.title">
                <div v-if="[dropdown.title] == 'Deep Drop Down'">
                  <v-row>
                    <v-menu offset-x left>
                      <template v-slot:activator="{ on }">
                        <v-btn
                          class="navigation-link navigation-btn pl-3 pr-1"
                          depressed
                          text
                          v-on="on"
                        >
                          <spam class="nav-dropdown">Deep Drop Down </spam>
                          <v-icon>mdi-chevron-left</v-icon>
                        </v-btn>
                      </template>
                      <v-list>
                        <v-list-item
                          v-for="deep in deep_drops"
                          :key="deep.title"
                        >
                          <v-list-item-content>
                            <a class="navigation-link" :href="deep.link">
                              {{ deep.title }}
                            </a>
                          </v-list-item-content>
                        </v-list-item>
                      </v-list>
                    </v-menu>
                  </v-row>
                </div>
                <div v-else>
                  <v-list-item-content>
                    <a class="navigation-link" :href="dropdown.link">
                      {{ dropdown.title }}
                    </a>
                  </v-list-item-content>
                </div>
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
        <div v-else>
          <v-btn
            class="nav-btn hidden-md-and-down"
            color="transparent"
            depressed
            text
          >
            <a class="nav-link" :href="btn.link">
              {{ btn.title }}
            </a>
          </v-btn>
        </div>
      </div>

      <v-app-bar-nav-icon
        class="hidden-lg-and-up"
        relative
        color="#fff"
        @click="drawer = !drawer"
      />
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app>
      <v-list>
        <v-btn icon class="float-right" @click.stop="drawer = false">
          <v-icon>mdi-window-close</v-icon>
        </v-btn>
        <v-list-item v-for="btn in btns" :key="btn.title">
          <div v-if="[btn.title] == 'Drop Down'">
            <v-row>
              <v-list-group>
                <template v-slot:activator>
                  <v-list-item-title class="navigation-dropdown">
                    Drop Down
                  </v-list-item-title>
                </template>
                <v-list-item v-for="dropdown in drops" :key="dropdown.title">
                  <div v-if="[dropdown.title] == 'Deep Drop Down'">
                    <v-row>
                      <v-list-group sub-group>
                        <template v-slot:activator>
                          <v-list-item-title class="navigation-dropdown">
                            Deep Drop Down
                          </v-list-item-title>
                        </template>
                        <v-list-item
                          v-for="deep in deep_drops"
                          :key="deep.title"
                        >
                          <v-list-item-content>
                            <a class="navigation-link" :href="deep.link">
                              {{ deep.title }}
                            </a>
                          </v-list-item-content>
                        </v-list-item>
                      </v-list-group>
                    </v-row>
                  </div>
                  <div v-else>
                    <v-list-item-content>
                      <a class="navigation-link" :href="dropdown.link">
                        {{ dropdown.title }}
                      </a>
                    </v-list-item-content>
                  </div>
                </v-list-item>
              </v-list-group>
            </v-row>
          </div>
          <div v-else>
            <v-list-item-content ml-4>
              <a class="navigation-link" :href="btn.link">
                {{ btn.title }}
              </a>
            </v-list-item-content>
          </div>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <footer>
      <div>
        <div class="links-box">
          <v-row>
            <v-col class="footer-col" lg="3" md="6" sm="6" cols="12">
              <span class="title-col">USEFUL LINKS</span>
              <div
                v-for="link in useful_links"
                :key="link"
                style="margin-top: 14px;"
              >
                <v-icon style="color: #5697d0; font-size: 18px;"
                  >mdi-chevron-right</v-icon
                >
                <a :href="link.link" style="text-decoration: none;">
                  <span class="link-text">{{ link.title }}</span>
                </a>
              </div>
            </v-col>
            <v-col class="footer-col" lg="3" md="6" sm="6" cols="12">
              <span class="title-col">OUR SERVICES</span>
              <div
                v-for="link in our_services"
                :key="link"
                style="margin-top: 14px;"
              >
                <v-icon style="color: #5697d0; font-size: 18px;"
                  >mdi-chevron-right</v-icon
                >
                <a :href="link.link" style="text-decoration: none;">
                  <span class="link-text">{{ link.title }}</span>
                </a>
              </div>
            </v-col>
            <v-col class="footer-col" lg="3" md="6" sm="6" cols="12">
              <span class="title-col">CONTACT US</span>
              <span class="footer-text"
                >A108 Adam Street <br />
                New York, NY 535022 <br />
                United States
              </span>
              <div class="footer-text">
                <span style="font-weight: bolder;">Phone:</span>
                <span> +1 5589 55488 55</span>
              </div>
              <div class="footer-text" style="margin-top: 0px;">
                <span style="font-weight: bolder;">Email:</span>
                <span> info@example.com</span>
              </div>
            </v-col>
            <v-col class="footer-col" lg="3" md="6" sm="6" cols="12">
              <span class="title-col">About Hidayah</span>
              <span class="footer-about"
                >Cras fermentum odio eu feugiat lide par naso tierra. Justo eget
                nada terra videa magna derita valies darta donna mare fermentum
                iaculis eu non diam phasellus.</span
              >
              <div class="socials-box">
                <button
                  v-for="social in socials"
                  :key="social"
                  class="social-button"
                  @click="redirect(social.link)"
                >
                  <v-icon style="color: #ffffff; font-size: 15px;">{{
                    social.icon
                  }}</v-icon>
                </button>
              </div>
            </v-col>
          </v-row>
        </div>
        <div class="copyright-box">
          <div class="footer-text" style="margin-top: 0px;">
            <span>© Copyright </span>
            <span style="font-weight: bolder;">Hidayah.</span>
            <span> All Rights Reserved</span>
          </div>
          <div class="footer-text" style="margin-top: 0px;">
            <span style="font-size: 13px;">Designed by </span>
            <a
              style="font-size: 13px; text-decoration: none; color: #428bca;"
              href="/"
            >
              BootstrapMade
            </a>
          </div>
        </div>
      </div>
    </footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      btns: [
        { title: 'Home', link: '/' },
        { title: 'About', link: '/' },
        { title: 'Services', link: '/' },
        { title: 'Portfolio', link: '/' },
        { title: 'Team', link: '/' },
        { title: 'Blog', link: '/' },
        { title: 'Drop Down', link: '/' },
        { title: 'Contact', link: '/' },
      ],
      drops: [
        { title: 'Drop Down 1', link: '/' },
        { title: 'Deep Drop Down', link: '/' },
        { title: 'Drop Down 2', link: '/' },
        { title: 'Drop Down 3', link: '/' },
        { title: 'Drop Down 4', link: '/' },
      ],
      deep_drops: [
        { title: 'Deep Drop Down 1', link: '/' },
        { title: 'Deep Drop Down 2', link: '/' },
        { title: 'Deep Drop Down 3', link: '/' },
        { title: 'Deep Drop Down 4', link: '/' },
        { title: 'Deep Drop Down 5', link: '/' },
      ],
      useful_links: [
        { title: 'Home', link: '/' },
        { title: 'About us', link: '/' },
        { title: 'Services', link: '/' },
        { title: 'Terms of service', link: '/' },
        { title: 'Privacy policy', link: '/' },
      ],
      our_services: [
        { title: 'Web Design', link: '/' },
        { title: 'Web Development', link: '/' },
        { title: 'Product Management', link: '/' },
        { title: 'Marketing', link: '/' },
        { title: 'Graphic Design', link: '/' },
      ],
      socials: [
        { icon: 'mdi-twitter', link: '/' },
        { icon: 'mdi-facebook', link: '/' },
        { icon: 'mdi-instagram', link: '/' },
        { icon: 'mdi-skype', link: '/' },
        { icon: 'mdi-linkedin', link: '/' },
      ],
    }
  },
  methods: {
    redirect(link) {
      window.location.href = link
    },
  },
}
</script>

<style scoped>
.nav-title {
  color: #fff;
  letter-spacing: 1px;
  font-size: 30px;
  font-family: 'Poppins', sans-serif;
}
.nav-btn:hover,
.navigation-btn:hover {
  color: transparent;
}
.nav-link {
  font-size: 12px;
  font-family: 'Open Sans', sans-serif;
  text-transform: uppercase;
  text-decoration: none;
  color: #fff;
  font-weight: 600;
}
.nav-link:hover,
.dropdown:hover,
.navigation-link:hover {
  color: #428bca;
}
.navigation-link {
  font-size: 15px;
  font-family: 'Open Sans', sans-serif;
  text-transform: none;
  text-decoration: none;
  color: black;
  margin-left: 2px;
}
.nav-dropdown,
.navigation-dropdown {
  font-size: 15px;
  font-family: 'Open Sans', sans-serif;
  letter-spacing: 0px;
  color: black;
  text-transform: none;
  display: flex;
}
.links-box {
  height: 340px;
  background-color: #272c30;
  display: flex;
  justify-content: center;
  padding-inline: 150px;
}
.copyright-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 110px;
  background-color: #2e3339;
}
.footer-col {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
}
.socials-box {
  display: flex;
  flex-direction: row;
  margin-right: 8px;
  margin-top: 10px;
}
.title-col {
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
  font-size: 16px;
  font-weight: bold;
  line-height: 1.2;
  margin-top: 50px;
}
.footer-text {
  font-family: 'Open Sans', sans-serif;
  color: #ffffff;
  font-size: 14px;
  font-weight: 400;
  margin-top: 20px;
  line-height: 26px;
}
.footer-about {
  margin-top: 20px;
  font-size: 14px;
  line-height: 24px;
  font-family: 'Raleway', sans-serif;
  color: #fff;
}
.link-text {
  color: #ffffff;
  font-size: 14px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
}
.link-text:hover {
  color: #5697d0;
}
.social-button {
  background-color: #394047;
  padding-inline: 10px;
  padding-block: 5px;
  border-radius: 4px;
  margin-right: 10px;
}
.social-button:hover {
  background-color: #428bca;
}

@media screen and (max-width: 1263px) {
  .links-box {
    height: 100%;
  }
}
</style>
