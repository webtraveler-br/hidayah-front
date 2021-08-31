<template>
  <div style="background-color: #fafafb;">
    <div class="header-box">
      <span class="header-text">
        CONTACT
      </span>
      <div>
        <span class="title-text">Get In Touch With </span>
        <span class="title-text" style="color: #428bca;">Us</span>
      </div>
      <span class="description-text"
        >Ut possimus qui ut temporibus culpa velit eveniet modi omnis est
        adipisci expedita at voluptas atque vitae autem.</span
      >
    </div>
    <v-row style="padding-bottom: 60px;">
      <v-col xl="6" lg="6" cols="12" class="col-box">
        <v-col xl="6" lg="6" md="6" cols="12" class="pa-0 ma-0">
          <div class="box-wrapper">
            <v-icon style="color: #92bce0; font-size: 50px;"
              >mdi-map-marker-outline</v-icon
            >
            <span class="box-title">ADDRESS</span>
            <span class="box-text">A108 Adam Street,</span>
            <span class="box-text">New York, NY 535022</span>
          </div>
          <div class="box-wrapper">
            <v-icon style="color: #92bce0; font-size: 50px;"
              >mdi-email-outline</v-icon
            >
            <span class="box-title">EMAIL US</span>
            <span class="box-text">contact@example.com</span>
            <span class="box-text">info@example.com</span>
          </div>
        </v-col>
        <v-col xl="6" lg="6" md="6" cols="12" class="pa-0 ma-0">
          <div class="box-wrapper">
            <v-icon style="color: #92bce0; font-size: 50px;"
              >mdi-phone-outline</v-icon
            >
            <span class="box-title">CALL US</span>
            <span class="box-text">+1 5589 55488 55</span>
            <span class="box-text">+1 5589 22548 64</span>
          </div>
          <div class="box-wrapper">
            <v-icon style="color: #92bce0; font-size: 50px;"
              >mdi-clock-outline</v-icon
            >
            <span class="box-title">WORKING HOURS</span>
            <span class="box-text">Mon - Fri: 9AM to 5PM</span>
            <span class="box-text">Sunday: 9AM to 1PM</span>
          </div>
        </v-col>
      </v-col>
      <v-col xl="6" lg="6" cols="12" class="col2-box">
        <v-row>
          <v-col xl="6" lg="6" md="6" cols="12">
            <div class="form-field">
              <span class="form-title">Your Name</span>
              <v-text-field
                class="form-input"
                v-model="contact.name"
                :rules="[(v) => !!v || 'Campo Obrigatório']"
                outlined
                dense
                background-color="#ffffff"
              />
            </div>
          </v-col>
          <v-col xl="6" lg="6" md="6" sm="12">
            <div class="form-field">
              <span class="form-title">Your Email</span>
              <v-text-field
                class="form-input"
                v-model="contact.email"
                :rules="[(v) => !!v || 'Campo Obrigatório']"
                outlined
                dense
                background-color="#ffffff"
              />
            </div>
          </v-col>
        </v-row>
        <div class="form-field">
          <span class="form-title">Subject</span>
          <v-text-field
            class="form-input"
            v-model="contact.subject"
            :rules="[(v) => !!v || 'Campo Obrigatório']"
            outlined
            dense
            background-color="#ffffff"
          />
        </div>
        <div class="form-field" style="margin-top: 10px;">
          <span class="form-title">Message</span>
          <v-textarea
            class="form-input"
            v-model="contact.message"
            :rules="[(v) => !!v || 'Campo Obrigatório']"
            outlined
            dense
            background-color="#ffffff"
          />
        </div>
        <div style="display: flex; justify-content: center;">
          <button class="button" @click="sendForm">Send Message</button>
        </div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contact: {
        name: '',
        email: '',
        subject: '',
        message: '',
      },
    }
  },
  methods: {
    sendForm() {
      if (
        this.contact.name &&
        this.contact.email &&
        this.contact.subject &&
        this.contact.message
      ) {
        const contact = {
          nome: this.contact.name,
          email: this.contact.email,
          assunto: this.contact.subject,
          mensagem: this.contact.message,
        }
        this.$axios
          .$post('message', contact)
          .then((res) => {
            window.alert('Mensagem enviada com sucesso!')
            this.contact.name = ''
            this.contact.email = ''
            this.contact.subject = ''
            this.contact.message = ''
          })
          .catch(({ response }) => {
            window.alert(
              'Ocorreu um erro \n' +
                Object.values(response.data.error).join('\n')
            )
          })
      } else window.alert('Existem campos obrigatórios não preenchidos!')
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
.col-box {
  display: flex;
  flex-direction: row;
  padding-left: 9vw;
}
.col2-box {
  padding-left: 30px;
  padding-right: 11vw;
}
.box-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: #fefefe;
  box-shadow: 0px 5px 90px 0px rgba(110, 123, 131, 0.1);
  padding-block: 2vw;
}
.box-title {
  font-size: 16px;
  font-weight: 600;
  font-family: 'Poppins', sans-serif;
  margin-top: 14px;
  margin-bottom: 5px;
  color: rgba(0, 0, 0, 0.87);
}
.box-text {
  font-size: 15px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
  margin-top: 2px;
  color: #444444;
}
.form-field {
  display: flex;
  flex-direction: column;
}
.form-title {
  font-family: 'Poppins', sans-serif;
  margin-bottom: 5px;
  color: #777777;
  font-size: 16px;
  font-weight: 400;
}
.form-input {
  font-size: 14px;
  font-weight: 400;
  color: #495057;
  font-size: 14px;
  font-family: 'Open Sans', sans-serif;
}
.button {
  background-color: #428bca;
  color: #ffffff;
  padding-block: 14px;
  padding-inline: 34px;
  margin-top: 15px;
  font-size: 16px;
  border-radius: 5px;
  margin-top: 10px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
  align-self: center;
  justify-self: center;
}
@media screen and (max-width: 1264px) {
  .col-box {
    padding-left: 0px;
  }
  .col2-box {
    padding-inline: 35px;
  }
}
@media screen and (max-width: 960px) {
  .col-box {
    flex-direction: column;
  }
}
</style>
